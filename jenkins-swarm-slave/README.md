
## 注意
因为有从容器内部访问外部 ```docker service``` 的需求，需要修改宿主机的```/var/run/docker.sock```文件访问权限.

```
sudo chmod a+rw /var/run/docker.sock
```

## 关于Environment

- INFRASTRUCTURE_CONF_GIT_TOKEN：访问git服务上私有的项目需要用到用户的认证/授权token，需要在启动镜像的时候export指定，获取token方法：
  
  1. 方法1: 登录git服务, 例如gitlab: 进入 Profile Settings->Account->Private Token,获取token
  2. 方法2: 命令行, 例如gitlab: `curl --request POST "${GIT_SERVICE}/api/v3/session?login={邮箱}&password={密码}"`

- 获取token后，在启动镜像前执行`export INFRASTRUCTURE_CONF_GIT_TOKEN=<your_git_service_token>`
