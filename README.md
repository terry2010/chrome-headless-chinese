基于 https://hub.docker.com/r/alpeware/chrome-headless-trunk  镜像简单修改后生成

仅添加供正常显示用的中文字体。 如果需要和windows显示效果一致，需要把windows字体拷到容器内

具体方法请自行搜索关键词
```
在 Ubuntu 18.04 LTS 上安装 Microsoft Windows 字体
```

如果可以在物理机上安装， 可以参考下面这个安装方式

https://github.com/terry2010/centos7-fast-init/tree/master/headless-chrome

### 启动方式

#### 当主机的docker 是host模式启动的时候，推荐使用传递参数的方式启动
```
docker run -it --rm -e DEBUG_ADDRESS="0.0.0.0" -e DEBUG_PORT="9226" -e CHROME_OPTS="--proxy-server=\"http=127.0.0.1:1080;https=127.0.0.1:10443\"" --net=host --name=chrome-headless-proxy -v /tmp/chromedata/:/data terry2010/chrome-headless-chinese
```

#### 当主机的docker 是bridge模式启动的时候，推荐使用转发端口方式启动

```
docker run -it --rm -p=0.0.0.0:9222:9222 --name=chrome-headless -v /tmp/chromedata/:/data terry2010/chrome-headless-chinese
```


Inspired by
- [beaufortfrancois](https://github.com/beaufortfrancois/download-chromium)
- [National Library of Norway](https://github.com/nlnwa/docker-chrome-headless)
