# 🚀 Laravel + Docker + Nginx + MySQL

This project provides a complete Laravel development environment using Docker, Nginx, and MySQL.

Application URL: http://localhost:8000

------------------------------------------------------------

## 📦 Tech Stack

- Laravel
- Docker
- Docker Compose
- Nginx
- MySQL 8.0

------------------------------------------------------------

## 🐳 Docker Services

1. **app** (`laravel_app`)
   - Built from Dockerfile
   - Working directory: /var/www
   - Project mounted as volume

2. **nginx** (`laravel_nginx`)
   - Image: nginx:latest
   - Port mapping: 8000 -> 80
   - Config loaded from docker/nginx
   - Depends on: laravel_app

3. **mysql** (`laravel_mysql`)
   - Image: mysql:8.0
   - Port: 3306
   - Credentials:
     - DB_DATABASE=laravel
     - DB_USERNAME=laravel
     - DB_PASSWORD=secret
     - MYSQL_ROOT_PASSWORD=secret

------------------------------------------------------------

## 🛠 Requirements

Make sure Docker and Docker Compose are installed:

docker --version  
docker compose version

------------------------------------------------------------

## 🚀 Setup Instructions

1. Clone the repository

git clone git@github.com:shikharbahikmagar/laravel_docker_nginx.git  
cd laravel_docker_nginx

2. Copy environment file

cp .env.example .env

3. Update `.env` database configuration:

DB_CONNECTION=mysql  
DB_HOST=mysql  
DB_PORT=3306  
DB_DATABASE=laravel  
DB_USERNAME=laravel  
DB_PASSWORD=secret

4. Build and start containers

docker compose up -d --build

5. Install Composer dependencies

docker compose exec laravel_app composer install

6. Generate application key

docker compose exec laravel_app php artisan key:generate

7. Run database migrations

docker compose exec laravel_app php artisan migrate

------------------------------------------------------------

## 🌐 Access Application

Open in browser: http://localhost:8000

------------------------------------------------------------

## 🛠 Useful Commands

Start containers:  
docker compose up -d

Stop containers:  
docker compose down

Rebuild containers:  
docker compose down  
docker compose up -d --build

Access app container shell:  
docker compose exec laravel_app bash

Run artisan command:  
docker compose exec laravel_app php artisan <command>

View logs:  
docker compose logs -f

------------------------------------------------------------

## ⚠ Reset Everything (Deletes Database Data)

docker compose down -v  
docker compose up -d --build

------------------------------------------------------------

## 📁 Project Structure

docker-compose.yml  
Dockerfile  
docker/nginx configuration  
Laravel project files

------------------------------------------------------------

Author: Shikhar Magar  
Laravel Developer
