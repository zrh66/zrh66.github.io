---
layout:     post
title:      Blog Changes
subtitle:    "\"看到最后哦🙈\""
date:       2018-01-15
author:     ZhangRuohan
header-img: img/post-bg-debug.png
catalog: true
tags:
    - 生活
    - Life
    - Blog
---


# 改变
这篇算是对Blog搭建的一个补充吧，毕竟搭起来容易，后续的维护和使用操作怎样顺手方便更重要。对！更重要！如果说出自一个DBA之口相信你一定会理解...🤷

主要对以下几点做出一点改进说明：

 - 搭建**jekyll**在本地调试**Blog**修改效果
 - 使用**GitHub Desktop**本地管理***repository***
 - 图床与图片上传工具的选择
 - **Markdown**编辑器选择与使用
 - 网站数据统计
 
# 过程

### 一. 本地调试**Blog**修改效果

>参考 [Run Jekyll on Windows][1]

#### **安装Ruby**
跟着文档点`Get Started` —> `Get Ruby for Windows`你会看到需要先安装**Ruby**环境（建议2.2以上）。
![Ruby下载][2]

然后跟着文档继续`Get the Ruby Devkit`,同样下载安装即可
![Ruby Devkit][3]

接着进入对应目录下初始化安装就可以啦：

```bash
$ ruby dk.rb init
$ ruby dk.rb install
```

#### **安装jekyll**
按照文档执行

```bash
$ gem install jekyll
```

会报错
> 参考 https://www.jianshu.com/p/9535334ffd54

    ERROR: Could not find a valid gem 'jekyll' (>= 0), here is why:
    Unable to download data from https://rubygems.org/ - SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B:certificate verify failed (https://api.rubygems.org/latest_specs.4.8.gz)
	
这是因为国外站点不稳定，国内有淘宝的镜像站点`https://ruby.taobao.org/`但是现在也已经不再维护了，现由 ruby-china 提供镜像服务，即我们要换

```bash
gem sources --add http://gems.ruby-china.org/ --remove https://rubygems.org/
```

然后再执行

```bash
$ gem install jekyll
$ gem install jekyll bundler
$ jekyll s
```

看到如下信息后说明你可以在 http://127.0.0.1:4000/访问自己的博客了，也就是说你不必每做一次修改就commit一次**GitHub**，本地调试好后用**GitHub Desktop**一次性push过去就OK了。
![jekyll][4]

### 二. 使用**GitHub Desktop**
>参考 https://desktop.github.com/

![GitHub Desktop][5]

整体来说没有什么安装难度，点一点就ok的东西。
使用也很简单：
 - 使用GitHub账号登陆
 - 将仓库clone到本地
 - 右键仓库可以有多种方式打开仓库文件进行修改
 - 修改后commit操作
 - 同步push至GitHub，同理如果GitHub有修改要先fetch到本地
![GitHub Desktop][6]
会实时显示出本地*repository*修改点，使用前记得同步fetch或push就好

### 三. 图床与图片上传工具的选择
关于图床的选择也比较多，Apple的就用iPic，Win最好选择国内的，加载速度快一些，如果不嫌麻烦的话尽量把图片压缩再上传，Blog的加载速度会更快一些，在手机上打开Blog时效果比较更明显。

 - 七牛云存储等
 - 微博
 - 极简图床，图床网，tuchuang001，img.so，LOFTER等等

我使用的是极简的Chrome插件绑定的微博作为图床，主要考虑微博比较稳定不会说没就没了，而且我的图片也不算多，用微博应该问题不大，不过建议还是用七牛云，10G免费，很多人推荐的。
 ![pic][7]
 
 
### 四. Markdown编辑器
 编辑器的话Win10自带很多，不过我还是选择了Cmd-Markdown😊
 原因是在知乎找的时候偶然看到了赖老师的评论：
 ![赖明星][8]
哈哈哈，活捉老师也是没谁了，老师推荐的当然很好用啊：无论是跟踪同步还是界面和功能，全都perfect。
![cmd][9]

### 五. 网站数据统计
这个就很简单了，只需要去百度统计注册一个账号，然后把自己的站点添加到自有网站中，再在获取代码中获取到`ba_track_id`
![baidu][10]

把这个再添加到_config文件中去就OK了
![ba_track_id][11]

# 花絮
整体完善下来差不多就是这样了，评论系统用的GitTalk，这里就不再叙述了，浏览器标签有个小彩蛋，点其他标签再看一下呢🙈
代码放在下面，喜欢就快拿去吧

```html
<script>
(function() {
    var OriginTitile = document.title, titleTime;
    document.addEventListener('visibilitychange', function() {
        if (document.hidden) {
            document.title = '死鬼去哪里了！';
            clearTimeout(titleTime);
        } else {
            document.title = '(つェ⊂)咦!又好了!';
            titleTime = setTimeout(function() {
                document.title = OriginTitile;
            },2000);
        }
    });
})();
</script>
```


  [1]: http://jekyll-windows.juthilo.com/
  [2]: https://ws1.sinaimg.cn/large/9e146039ly1fnhem116kqj20fc09aq32.jpg
  [3]: https://ws1.sinaimg.cn/large/9e146039ly1fnhey529hyj20c4056a9z.jpg
  [4]: https://ws1.sinaimg.cn/large/9e146039ly1fnhftp0s0ej20hy05ot8q.jpg
  [5]: https://ws1.sinaimg.cn/large/9e146039ly1fnhg40k0dqj210u0gxwfh.jpg
  [6]: https://ws1.sinaimg.cn/large/9e146039ly1fnhgn655hvj211y0k7ac1.jpg
  [7]: https://ws1.sinaimg.cn/large/9e146039ly1fnhh3b4uhqj210u0gx0sy.jpg
  [8]: https://ws1.sinaimg.cn/large/9e146039ly1fnhhj6lu61j20c102qdft.jpg
  [9]: https://ws1.sinaimg.cn/large/9e146039ly1fnhhn26jnij211y0jlmzv.jpg
  [10]: https://ws1.sinaimg.cn/large/9e146039ly1fnhi1tkfa6j210u0gxwg8.jpg
  [11]: https://ws1.sinaimg.cn/large/9e146039ly1fnhi40r5mdj20ab02d3yb.jpg