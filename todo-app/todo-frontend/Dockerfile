FROM node:20.5.1-bookworm-slim AS build-stage
WORKDIR /usr/src/app
COPY . .
RUN npm ci
# NGINX replaces the communication line between the frontend and backend
# ENV VITE_BACKEND_URL="//localhost:3000"
ENV VITE_BACKEND_URL="//localhost:8080/api/"
RUN npm run build

FROM nginx:1.25-alpine
COPY --from=build-stage /usr/src/app/dist /usr/share/nginx/html
EXPOSE 80