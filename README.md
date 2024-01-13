# 使用 Docker 安装 V2Board

### 安装 Docker
```
curl -fsSL https://get.docker.com | bash
curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod a+x /usr/local/bin/docker-compose
# 创建个软链接，以后用 dc 命令来代替 docker-compose
rm -rf which dc  # 若系统中存在 dc 则删除，这个 dc 就是个计算器，完全没有用
ln -s /usr/local/bin/docker-compose /usr/bin/dc
```

### 克隆代码
```
git clone https://github.com/v2board/v2board-docker.git
cd v2board-docker/
git submodule update --init
echo '  branch = dev' >> .gitmodules
git submodule update --remote
```

### 启动环境

```
dc up -d
```

### 安装配置 V2Board
```
dc exec www bash
bash-5.0# wget https://getcomposer.org/download/1.9.0/composer.phar
bash-5.0# php composer.phar install
bash-5.0# php artisan v2board:install

数据库地址： mysql
数据库名：v2board
数据库用户名：root
数据库密码：v2boardisbest

```
