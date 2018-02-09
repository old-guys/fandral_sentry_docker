## Sentry docker 镜像

- https://sentry.io/
- https://docs.docker.com/compose/networking/#specify-custom-networks
- https://docs.docker.com/compose/compose-file/#volumes
- https://docs.docker.com/engine/reference/commandline/volume_create/#related-commands
- https://sentry.io/pricing/
- https://docs.sentry.io/
- https://hub.docker.com/_/sentry/
- https://store.docker.com/images/sentry

## 配置镜像启动脚本

这里是容器里面的启动脚本需要手动配置 `/acs/conf/ews_startup.sh` 可以参见

```shell
cp docker-compose.yml.example docker-compose.yml
```

### Setup Sentry services

```shell
# Generate a new secret key to be shared by all sentry containers
docker-compose run sentry_worker config generate-secret-key

# If this is a new database, you'll need to run upgrade
# Configuring the initial user
docker-compose run sentry_worker upgrade

# Configuring the initial user
docker-compose run sentry_worker createuser

docker-compose exec -it sentry_worker bash

# debug
docker exec -it sentry_worker bash

# run command options
docker-compose run sentry_worker "--help
```

## 服务访问地址

```shell
# web
http://localhost:8080/
```