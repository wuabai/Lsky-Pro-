搭建教程

cd /home/

git clone https://github.com/Yuri-NagaSaki/ImageFlow && cd ImageFlow

docker compose up -d

docker-compose up -d

注意，数据库连接地址，填docker-compose文件里的容器名称lsky-pro-db，连接端口不用填。

docker-compose.yml

version: '3'
services:
    lsky-pro:
        container_name: lsky-pro
        image: wuabai/lsky-pro
        restart: always
        volumes:
            - /home/lsky-pro/lsky-pro-data:/var/www/html  #映射到本地
        ports:
            - 869:80
        environment:
            - MYSQL_HOST=mysql
            - MYSQL_DATABASE=lsky-pro
            - MYSQL_USER=lsky-pro
            - MYSQL_PASSWORD=lsky-pro

    mysql:
        image: mysql:8.0
        container_name: lsky-pro-db
        restart: always
        environment:
          - MYSQL_DATABASE=lsky-pro
          - MYSQL_USER=lsky-pro
          - MYSQL_PASSWORD=lsky-pro
          - MYSQL_ROOT_PASSWORD=lsky-pro
        volumes:
          - /home/lsky-pro/db:/var/lib/mysql

