FROM node:18 AS builder

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . . 

RUN npm run build 

FROM nginx:alpine AS production 

COPY --from=builder /app/dist/angular/browser /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx-debug", "-g", "daemon off;" ]