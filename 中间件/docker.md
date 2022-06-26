###  portainer(容器管理工具)
```bas
docker run --name portainer -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```
### Nginx
 ####    先进行文件拷贝
```bash
docker run --name nginx -p 9001:80 -d nginx
 将容器nginx.conf文件复制到宿主机
docker cp nginx:/etc/nginx/nginx.conf /home/app/Nginx/conf/nginx.conf
 将容器conf.d文件夹下内容复制到宿主机
docker cp nginx:/etc/nginx/conf.d /home/app/Nginx/conf/conf.d
 将容器中的html文件夹复制到宿主机
docker cp nginx:/usr/share/nginx/html /home/app/Nginx/
```
 ####      执行
```bash
docker run \
-p 80:80 \
--name nginxweb \
-v /home/app/Nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
-v /home/app/Nginx/conf/conf.d:/etc/nginx/conf.d \
-v /home/app/Nginx/logs:/var/log/nginx \
-v /home/app/Nginx/html:/usr/share/nginx/html \
-d nginx:latest
```
###  安装MySQL
```bash
docker run -p 3306:3306 --name mysql8.0 \
-v /home/app/MySQL/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=363764393 \
-itd mysql:8.0
```
###  Redis
```bash
docker run -itd --name redis -p 6379:6379 redis:6.2.6 redis-server --requirepass "363764393"
```
###  mongo
```bash
docker run -d -p 27017:27017 -v /home/app/MongoDB/configdb:/data/configdb -v /home/app/MongoDB/db:/data/db --name mongo mongo:5.0
```
### 服务运行
```bash
nohup python3 -u /home/Codebase/python/app.py >/home/Codebase/python/null 2>&1 & #后台运行python
ps -ef | grep python3 #查看后台
tail -f null #查看日记
nohup python3 -u /home/python/ibox.py >/home/python/null 2>&1 & #后台运行python
```





