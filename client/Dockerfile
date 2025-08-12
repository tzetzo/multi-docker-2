# Build stage
FROM node:lts-alpine as build

WORKDIR /app

COPY package.json ./
RUN npm install

COPY . .

RUN npm run build

# Production stage
FROM nginx

COPY ./nginx/prod.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/build /usr/share/nginx/html
