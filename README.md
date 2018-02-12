# PHP App Docker Environment

本项目通过以Yii2框架的为例,来构建出基于Docker,Nginx,PHP的环境,并扩展出如Mysql,Redis等常见的配套运行环境.

## 特点

1. 采用alpine基础环境,包比较小
2. 针对great wall,包管理镜像都已经设置为国内镜像.

## 快速使用

请先在宿主机安装好git,docker环境,下载本项目

* 环境文件

根目录.env为docker-compose的环境配置文件,可根据需求变更其内容.

* docker-compose构建

```cmd
docker-composer build
//或者通过up自动构建并启动
docker-compose up
```

## docker环境安装

安装移步官网

* docker https://docs.docker.com/engine/installation/
* docker-compose https://docs.docker.com/compose/install/

注意：Docker安装要求Linux 3.10以上版本，用uname -a命令可查看到。

## 国内用户请注意使用国内镜像以加快构建

## 框架

从网上借了张架构类似的图:  
![结构图](https://sfault-image.b0.upaiyun.com/163/377/1633775139-56455bf065b3d_articlex)
## 目录说明

```text
.
|-- .env                                    环境配置文件
|-- docker-composer.yml                     容器启动配置文件
|-- docker-composer.fpm-nginx.yml           web容器配置文件
|-- php                                     PHP镜像目录
|   |-- Dockerfile-alpine                   构建文件
|   |-- images-files                        需要进入镜像的文件,配置文件或执行文件
|       |-- usr/local/bin
|           |-- composer                    composer脚本
|           |-- docker-php-entrypoint       php容器入口脚本
|-- nginx
|   |-- Dockerfile-alpine                   构建文件
|   |-- images-files                        需要进入镜像的文件,配置文件或执行文件
|       |-- etc/nginx/nginx.conf            nginx主配置文件,一般不包含server节
|       |-- etc/nginx/conf.d/               站点配置目录.
|   |-- docker-nginx-entrypoint             nginx容器入口脚本
|-- config                                  运行时自定义配置目录
|   |-- nginx                               nginx站点配置目录,包含了一个测试配置
|-- www                                     站点目录
|   |-- app/                                测试站点,包含了一个显示phpinfo的文件
|-- log                                     日志目录
|   |-- php                                 PHP日志的目录
|   |-- nginx                               nginx日志目录
```
