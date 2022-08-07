# Quick Docker Symfony

This repository will allow you to start a Symfony project **very quickly** 
with PostgreSQL 14, pgAdmin 4 and one of three php versions: 
- 7.4.3
- 8.0.9
- 8.1.8

For ease of use, ports, containers and networks
**have the abbreviated name** of the php version in their name: 743, 809 and 818.

# Peculiarities
* inside the container you will be as user `app`
* available: xdebug, composer, nano, mc, curl, wget
* credentials can be found in the `.env` file

## Compliance

Between php and Symphony versions

| #   | php | Symfony |
|-----|-----|---------|
| 1   |  7.4.3   | 5.4.11     |
| 2   |  8.0.9   | 6.0.11     |
| 3   |  8.1.8   | 6.1.3     |

## Usage

**Step #1**: build php-image and run project as daemon
> docker-compose up -d --build

**Step #2**: enter into php container
> docker exec -it php743 bash  
> docker exec -it php809 bash  
> docker exec -it php818 bash

**Step #3**: install dependencies
> composer install

Steps #2 and #3 can be combined into one
> docker exec -it php743 composer install

Voila! All is ready!

# Hints
```shell
docker-compose up -d --build
docker exec -it php743 bash

docker container rename php743 pre_php743
docker container rename web743 pre_web743
docker container rename db743 pre_db743
docker stop pre_php743 pre_web743 pre_db743

docker cp php743:/path/to/container/file.txt .
docker cp file.txt php743:/path/to/container/directory

docker rm $(docker ps -aq) -f
docker rmi $(docker images -q) -f

docker-compose down -v
```
