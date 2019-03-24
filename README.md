# sougouweixin
爬取数据以及实现数据可视化
What is weixin_crawler?

weixin_crawler是一款使用Scrapy、Flask、Echarts、Elasticsearch等实现的微信公众号文章爬虫，自带分析报告(报告样例)和全文检索功能，几百万的文档都能瞬间搜索。weixin_crawler设计的初衷是尽可能多、尽可能快地爬取微信公众的历史发文

如果你想先看看这个项目是否有趣，这段不足3分钟的介绍视频一定是你需要的：

https://www.youtube.com/watch?v=CbfLRCV7oeU&t=8s
免部署马上体验公众号数据采集

通过免安装可执行程序WCplus.exe https://shimo.im/docs/E1IjqOy2cYkPRlZd 可马上体验weixin_crawler的数据采集功、导出Excel和PDF功能
主要特点

    使用Python3编写

    爬虫框架为Scrapy并且实际用到了Scrapy的诸多特性，是深入学习Scrapy的不错开源项目

    利用Flask、Flask-socketio、Vue实现了高可用性的UI界面。功能强大实用，是新媒体运营等岗位不错的数据助手

    得益于Scrapy、MongoDB、Elasticsearch的使用，数据爬取、存储、索引均简单高效

    支持微信公众号的全部历史发文爬取

    支持微信公众号文章的阅读量、点赞量、赞赏量、评论量等数据的爬取

    自带面向单个公众号的数据分析报告

    利用Elasticsearch实现了全文检索，支持多种搜索和模式和排序模式，针对搜索结果提供了趋势分析图表

    支持对公众号进行分组，可利用分组数据限定搜索范围

    原创手机自动化操作方法，可实现爬虫无人监管

    反爬措施简单粗暴

使用到的主要工具
语言 		Python3.6
前端 	web框架 	Flask / Flask-socketio / gevent
	js/css库 	Vue / Jquery / W3css / Echarts / Front-awsome
后端 	爬虫 	Scrapy
	存储 	Mongodb / Redis
	索引 	Elasticsearch
运行方法

weixin_crawler已经在Win/Mac/Linux系统下运行成功, 建议优先使用win系统尝试 weixin_crawler could work on win/mac/linux, although it is suggested to try on win os firstly

Insatall mongodb / redis / elasticsearch and run them in the background

    downlaod mongodb / redis / elasticsearch from their official sites and install them

    run them at the same time under the default configuration. In this case mongodb is localhost:27017 redis is localhost:6379(or you have to config in weixin_crawler/project/configs/auth.py)

    Inorder to tokenize Chinese, elasticsearch-analysis-ik have to be installed for Elasticsearch

Install proxy server and run proxy.js

    install nodejs and then npm install anyproxy and redis in weixin_crawler/proxy

    cd to weixin_crawler/proxy and run node proxy.js

    install anyproxy https CA in both computer and phone side

    if you are not sure how to use anyproxy, here is the doc

Install the needed python packages

    NOTE: you may can not simply type pip install -r requirements.txt to install every package, twisted is one of them which is needed by scrapy. When you get some problems about installing python package(twisted for instance), here always have a solution——downlod the right version package to your drive and run $ pip install package_name

    I am not sure if your python enviroment will throw other package not found error, just install any package that is needed

Some source code have to be modified(maybe it is not reasonable)

    scrapy Python36\Lib\site-packages\scrapy\http\request\ _init_.py --> weixin_crawler\source_code\request\__init__.py

    scrapy Python36\Lib\site-packages\scrapy\http\response\ _init_.py --> weixin_crawler\source_code\response\_init_.py

    pyecharts Python36\Lib\site-packages\pyecharts\base.py --> weixin_crawler\source_code\base.py. In this case function get_echarts_options is added in line 106

If you want weixin_crawler work automatically those steps are necessary or you shoud operate the phone to get the request data that will be detected by Anyproxy manual

    Install adb and add it to your path(windows for example)

    install android emulator(NOX suggested) or plugin your phone and make sure you can operate them with abd from command line tools

    If mutiple phone are connected to your computer you have to find out their adb ports which will be used to add crawler

    adb does not support Chinese input, this is a bad news for weixin official account searching. In order to input Chinese, adb keyboard has to be installed in your android phone and set it as the default input method, more is here

Why could weixin_crawler work automatically? Here is the reason:

    If you want to crawl a wechat official account, you have to search the account in you phone and click its "全部消息" then you will get a message list , if you roll down more lists will be loaded. Anyone of the messages in the list could be taped if you want to crawl this account's reading data
    If a nickname of a wechat official account is given, then wexin_crawler operate the wechat app installed in a phone, at the same time anyproxy is 'listening background'...Anyway weixin_crawler get all the request data requested by wechat app, then it is the show time for scrapy
    As you supposed, in order to let weixin_crawler operate wechat app we have to tell adb where to click swap and input, most of them are defined in weixin_crawler/project/phone_operate/config.py. BTW phone_operate is responsible for wechat operate just like human beings, its eyes are baidu OCR API and predefined location tap area, its fingers are adb

    Run the main.py

    $ cd weixin_crawler/project/

    $ python(3) ./main.py

    Now open the browser and everything you want would be in localhost:5000.

    In this long step list you may get stucked, join our community for help, tell us what you have done and what kind of error you have found.

    Let's go to explore the world in localhost:5000 together

功能展示

UI主界面

1

添加公众号爬取任务和已经爬取的公众号列表

1

爬虫界面

设置界面

公众号历史文章列表

报告

搜索

加入社区

也许你属于：

    刚刚毕业的技术小白，没啥项目开发经验

    能轻松让weixin_crawler跑起来的老司机

    爬虫大牛，指哪儿爬哪儿
