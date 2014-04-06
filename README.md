blog_toolsbox
=============

在学习使用Jekyll搭建个人博客时候写的一些工具，作为学习积累哈哈



### 一.简易Jekyll调试脚本 v0.1

- 自动启动 jekyll build --watch
- 自动启动 jekyll serve 
- 自动启动firefox 并且打开localhost:4000


```
#!/bin/bash
#制定路径
Path=$1
Build_serve_path=${Path:-"/home/yg/ganx/ygyg503.github.com/"} #给默认值
echo "$Build_serve_path"
#左边成功 右边才执行
cd $Build_serve_path && jekyll build --watch &

#上面成功下面才会执行
if [ $? -eq '0' ];then
    echo "xxxxxxx"
    pwd
    firefox localhost:4000 &
    cd $Build_serve_path 
    jekyll serve 
fi
```

---

### 二.简单的_Post文章管理脚本 v1.0

- 方便查看_posts目录文章
- 便利增加文件，并自动调用gedit编辑器修改
- 删除文章，自动将文章移动到_recycle文件夹

基本使用格式如下:

```
格式
script_name.sh  jekyll_path edit_type blog_name 
script_name.sh  jekyll路径   操作类型   操作文件名

参数
- jekyll_path: 可以选择用`def`或者你的本地jekyll路径
- edit_type: 可以选择 new（新建或修改）,del（删除），ls(查看) 
- blog_name: 新建的需要给一个文件名，不给参数将以日期为默认文章名

例子

$ ./edit_blog.sh def new my_new_blog

```


---
