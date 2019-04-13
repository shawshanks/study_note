# 项目名称:学习笔记
## 1.项目简介
我们要编写一个名为"学习笔记"的Web应用程序,让用户能够记录感兴趣的主题,并在学习每个主题的过程中添加日志条目.
"学习笔记"的主页对这个网站进行描述,并邀请用户注册或登录. 用户登录后, 就可以创建新主题,添加条目以及阅读已有的条目.
## 2. 项目设计功能
1. 用户可以注册,登陆和注销.
2. 用户可以添加主题, 添加条目(内容), 编辑已有内容.
3. 禁止未登录的用户访问除主页以外的页面.
4. 已登陆用户只可访问自己的数据.

## 3. 涉及到的技术
1. 虚拟环境的创建和管理.
2. 使用Git/GitHub管理代码.
3. 使用HTML/css创建模板.
4. MySQL数据库的链接.
5. 使用boot-strap3应用对模板外观进行优化.
6. 使用Heroku部署项目.

## 4. 使用到的Django知识
1. url的反向解析 [URL调度器](http://python.usyiyi.cn/django/topics/http/urls.html)
 - 作用:
 使用相对链接, 避免生成硬链接, 要修改项目中的URL, 只需修改urls.py中的URL模式. 易于日后的修改和维护.
2. 表单

## 5.项目进行中遇到的坑 :sob:
### 1. 项目部署
 使用`git push hero master`命令推送到Heroku创建的库中时, 没有添加 Procfile文件,导致推送后出现` code=H14 desc="No web processes running" `错误.  并且使用`heroku ps:scale web=1` 出现 `Couldn't find that formation.`
  
  注:
 1. [Heroku Error Codes](https://devcenter.heroku.com/articles/error-codes#h14-no-web-dynos-running)
 2. Pracefile作用: 告诉Heroku启动哪些进程, 以便能正确地提哦那个项目提供的服务.
 
### 2. 添加错误页面之后,对settings.py的设置
```
TEMPLATE =[
    { 
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'learning_log/templates')],
        'APP_DIRS': True,
        --snip--
     },
]
```
误将 `learning_log`写为`learning_logs`导致调试不过关. 因为路径错误, 所以Django找不到错误模板的所在地.
其实不写`learning_log`也可

### 2. 关于同时push代码至github和heroku
因为是在pycharm中创建和开始项目的, 而项目完成后需要部署到heroku中, 同时又要提交到github. 正确的姿势应该是:
 1. 先将代码添加和提交`git add`和`git commit`.
 2. 然后先使用`git push heroku master`将代码提交至heroku.
 




