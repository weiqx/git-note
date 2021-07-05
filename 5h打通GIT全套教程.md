**Reference**   https://www.bilibili.com/video/BV1vy4y1s7k6?t=4&p=26

## 课程介绍

1、Git

Git介绍	Git安装	Git命令	Git分支	Idea 集成Git

2、Github

创建远程库	代码推送 Push	代码拉取 Pull	代码克隆 Clone	SSH免密登录	Idea集成GitHub

3、Gitee码云

码云创建远程库	Idea集成Gitee码云	码云连接GitHub 进行代码的复制和迁移

4、Gitlab	Gitlab服务器的搭建与部署	Idea集成Gitlab

课程目标：5小时熟练掌握 Git Github Gitlab Gitee 的使用



## 第1章 Git 概述

​		Git 是一个免费的、开源的分布式版本控制系统，可以快速高效地处理从小型到大型的各种项目。
​		Git 易于学习，占地面积小，性能极快。 它具有廉价的本地库，方便的暂存区域和多个工作流分支等特性。 其性能优于 Subversion、 CVS、 Perforce 和 ClearCase 等版本控制工具。

### 1.1 何为版本控制

​		版本控制是一种记录文件内容变化，以便将来查阅特定版本修订情况的系统。
​		版本控制其实最重要的是可以记录文件修改历史记录，从而让用户能够查看历史版本，方便版本切换。



![1625412474001](C:\Users\86568\AppData\Roaming\Typora\typora-user-images\1625412474001.png)

### 1.2 为什么需要版本控制

​		个人开发过渡到团队协作。 

### 1.3 版本控制工具 

**集中式版本控制工具** 

​		CVS、 SVN(Subversion)、 VSS……
​		集中化的版本控制系统诸如 CVS、 SVN 等，都有一个单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。多年以来，这已成为版本控制系统的标准做法。
​		这种做法带来了许多好处，每个人都可以在一定程度上看到项目中的其他人正在做些什么。而管理员也可以轻松掌控每个开发者的权限，并且管理一个集中化的版本控制系统， 要远比在各个客户端上维护本地数据库来得轻松容易。
​		事分两面，有好有坏。这么做显而易见的缺点是中央服务器的单点故障。如果服务器宕机一小时，那么在这一小时内，谁都无法提交更新，也就无法协同工作。 

**分布式版本控制工具**

​		==Git==、 Mercurial、 Bazaar、 Darcs……
像 Git 这种分布式版本控制工具，客户端提取的不是最新版本的文件快照，而是把代码仓库完整地镜像下来（本地库）。这样任何一处协同工作用的文件发生故障，事后都可以用其他客户端的本地仓库进行恢复。因为每个客户端的每一次文件提取操作，实际上都是一次
对整个文件仓库的完整备份。
​		分布式的版本控制系统出现之后,解决了集中式版本控制系统的缺陷:

​		1. 服务器断网的情况下也可以进行开发（因为版本控制是在本地进行的）

​		2. 每个客户端保存的也都是整个完整的项目（包含历史记录， 更加安全） 

### 1.4 Git 简史 

### 1.5 Git 工作机制 



![1625412914041](C:\Users\86568\AppData\Roaming\Typora\typora-user-images\1625412914041.png)



### 1.6 Git 和代码托管中心 



代码托管中心是基于网络服务器的远程代码仓库，一般我们简单称为远程库。
➢ 局域网
		✓ GitLab
➢ 互联网
		✓ GitHub（外网）
		✓ Gitee 码云（国内网站） 

## 第2章 Git 安装 

​		官网地址： https://git-scm.com/

​		查看 GNU 协议，可以直接点击下一步。 

## 第 3 章 Git 常用命令 

vim文件操作

```bash
vim hello.txt  -- 创建文件

i   --进入insert模式

esc退出insert模式
yy 复制
p  粘贴

:wq 回车   保存并退出vim
```

linux命令

```bash
cat hello.txt  -- 查看文件
tail -n 1 hello.txt  -- 查看文件最后一行




```

==Git命令==

```bash
git status
git add hello.txt  -- 添加暂存区
git commit hello.txt  -- 提交版本库

vim hello.txt   -- 修改文件
git status    -- modified

git reflog   -- 查看版本信息
git log      -- 查看详细版本信息
```



| 命令名称                             | 作用           |
| ------------------------------------ | -------------- |
| git config --global user.name 用户名 | 设置用户签名   |
| git config --global user.email 邮箱  | 设置用户邮箱   |
| git init                             | 初始化本地库   |
| git status                           | 查看本地库状态 |
| git add 文件名                       | 添加到暂存区   |
| git commit -m "日志信息" 文件名      | 提交到本地库   |
| git reflog                           | 查看历史记录   |
| git reset --hard 版本号              | 版本穿梭       |

### 3.1 设置用户签名 



```bash
1）基本语法 
git config --global user.name 用户名
git config --global user.email 邮箱

2）案例实操
全局范围的签名设置：
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/git-demo (master)
$ git config --global user.name git-demo
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/git-demo (master)
$ git config --global user.email 865684885@qq.com
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/git-demo (master)
$ cat ~/.gitconfig
[user]
    name = Layne
    email = Layne@atguigu.com

```



说明：
		签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看
到，以此确认本次提交是谁做的。 Git 首次安装必须设置一下用户签名，否则无法提交代码。
		==注意==： 这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任
何关系。 



### 3.2 初始化本地库 

1） 基本语法
`git init`
2）案例实操 

```bash
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720
$ git init
Initialized empty Git repository in D:/Git-Space/SH0720/.git/
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720 (master)
$ ll -a
total 4
drwxr-xr-x 1 Layne 197609 0 11 月 25 14:07 ./
drwxr-xr-x 1 Layne 197609 0 11 月 25 14:07 ../
drwxr-xr-x 1 Layne 197609 0 11 月 25 14:07 .git/ （.git 初始化的效
果， 生成 git）
```

3）结果查看 

### 3.3 查看本地库状态 

1） 基本语法 

`git status`

2）案例实操 

**3.3.1 首次查看（工作区没有任何文件）** 

```bash
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720 (master)
$ git status
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```

**3.3.2 新增文件（hello.txt）**

```bash
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720 (master)
$ vim hello.txt
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
hello git! hello atguigu!
```

**3.3.3 再次查看（检测到未追踪的文件）** 

```bash
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720 (master)
$ git status
```

### 3.4 添加暂存区

**3.4.1 将工作区的文件添加到暂存区**

1）基本语法
`git add` 文件名
2）案例实操 

`git add hello.txt`

**3.4.2 查看状态（检测到暂存区有新文件）** 

`git status`

### 3.5 提交本地库

**3.5.1 将暂存区的文件提交到本地库**

1）基本语法
`git commit -m` "日志信息" 文件名
2）案例实操 

```bash
git commit -m "my first commit" hello.txt
```

**3.5.2 查看状态（没有文件需要提交）** 

`git status`

### 3.6 修改文件（hello.txt） 

`vim hello.txt`

**3.6.1 查看状态（检测到工作区有文件被修改）** 

`git status`

**3.6.2 将修改的文件再次添加暂存区** 

`git add hello.txt`

**3.6.3 查看状态（工作区的修改添加到了暂存区）** 

`git status `



### 3.7 历史版本 

**3.7.1 查看历史版本**

1 基本语法

`git reflog `         查看版本信息

`git log `		查看版本详细信息

2 案例实操



**3.7.2 版本穿梭**

1）基本语法
`git reset --hard 版本号`
2）案例实操 



**Git 切换版本， 底层其实是移动的 HEAD 指针。**



## 第 4 章 Git 分支操作 

### 4.1 什么是分支 

​		在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独分支。使用分支意味着程序员可以把自己的工作从开发主线上分离开来， 开发自己分支的时候，不会影响主线分支的运行。对于初学者而言，分支可以简单理解为副本，一个分支就是一个单独的副本。（分支底层其实也是指针的引用） 

### 4.2  分支的好处

​		同时并行推进多个功能开发，提高开发效率。
​		各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

### 4.3 分支的操作

| 命令名称            | 作用                         |
| ------------------- | ---------------------------- |
| git branch 分支名   | 创建分支                     |
| git branch -v       | 查看分支                     |
| git checkout 分支名 | 切换分支                     |
| git merge 分支名    | 把指定的分支合并到当前分支上 |

**4.3.1 查看分支**

1 基本语法

`git branch -v`
2 案例实操



**4.3.2  创建分支**

1 基本语法

`git branch  分支名`

2 案例实操

```bash
git branch hot-fix
git branch -v
```



**4.3.3  修改分支**

```bash
$ vim hello.txt

$ git add hello.txt

$ git commit -m "my forth commit" hello.txt

$ git branch -v
```



**4.3.4 切换分支** 

1）基本语法
`git checkout 分支名`
2）案例实操 

```bash
$ git checkout hot-fix

$ cat hello.txt

--在 hot-fix 分支上做修改
```



**4.3.5 合并分支** 

1） 基本语法
git merge 分支名
2） 案例实操 在 master 分支上合并 hot-fix 分支 

```bash
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720 (master)      
$ git merge hot-fix
```



**4.3.6 产生冲突** 

冲突产生的原因：
合并分支时，两个分支在==同一个文件的同一个位置==(???)有两套完全不同的修改。 Git 无法替我们决定使用哪一个。必须人为决定新代码内容。
查看状态（检测到有文件有两处修改） 



**4.3.7 解决冲突** 



### 4.4 创建分支和切换分支图解 



## 第 5 章 Git 团队协作机制

### 5.1 团队内协作 





### 5.2 跨团队协作 

## 第 6 章  GitHub  操作

GitHub 网址： https://github.com/

Ps:全球最大同性交友网站， 技术宅男的天堂， 新世界的大门， 你还在等什么?

| 账号               | 姓名     | 验证邮箱                   |
| ------------------ | -------- | -------------------------- |
| atguiguyueyue      | 岳不群   | atguiguyueyue@aliyun.com   |
| atguigulinghuchong | 令狐冲   | atguigulinghuchong@163.com |
| atguigudongfang1   | 东方不败 | atguigudongfang@163.com    |

注:此三个账号为讲师使用账号， 同学请自行注册， 然后三个同学为一组进行团队协作！



### 6.1  创建远程仓库



### 6.2 远程仓库操作 

| 命令名称                           | 作用                                                      |
| ---------------------------------- | --------------------------------------------------------- |
| git remote -v                      | 查看当前所有远程地址别名                                  |
| git remote add 别名 远程地址       | 起别名                                                    |
| git push 别名 分支                 | 推送本地分支上的内容到远程仓库                            |
| git clone 远程地址                 | 将远程仓库的内容克隆到本地                                |
| git pull 远程库地址别名 远程分支名 | 将远程仓库对于分支最新内容拉下来后与 当前本地分支直接合并 |



**6.2.1 创建远程仓库别名**
1） 基本语法
git remote -v 查看当前所有远程地址别名
git remote add 别名 远程地址
2）案例实操 



**6.2.2 推送本地分支到远程仓库**
1） 基本语法
git push 别名 分支
2） 案例实操 



**6.2.3 克隆远程仓库到本地**
1） 基本语法
`git clone 远程地址`
2）案例实操 



**6.2.4 邀请加入团队**
1） 选择邀请合作者 

2） 填入想要合作的人 

3 ） 复 制 地 址 并 通 过 微 信 钉 钉 等 方 式 发 送 给 该 用 户 ， 复 制 内 容 如 下 ：
https://github.com/atguiguyueyue/git-shTest/invitations 

4） 在 atguigulinghuchong 这个账号中的地址栏复制收到邀请的链接，点击接受邀请。 

5） 成功之后可以在 atguigulinghuchong 这个账号上看到 git-Test 的远程仓库。 

6） 令狐冲可以修改内容并 push 到远程仓库。 

7） 回到 atguiguyueyue 的 GitHub 远程仓库中可以看到，最后一次是 lhc 提交的。 



6.2.5 **拉取远程库内容**
1） 基本语法
`git pull 远程库地址别名 远程分支名`          -- 分支名是指的远程分支名 还是 本地库的分支名？？

2）案例实操 



### 6.3 跨团队协作

1） 将远程仓库的地址复制发给邀请跨团队协作的人，比如东方不败。 

2） 在东方不败的 GitHub 账号里的地址栏复制收到的链接，然后点击 Fork 将项目叉到自己的本地仓库。 

3） 东方不败就可以在线编辑叉取过来的文件。 

4） 编辑完毕后，填写描述信息并点击左下角绿色按钮提交。 

5） 接下来点击上方的 Pull 请求，并创建一个新的请求。 

6） 回到岳岳 GitHub 账号可以看到有一个 Pull request 请求。 

7） 如果代码没有问题，可以点击 Merge pull reque 合并代码。 



### 6.4 SSH 免密登录

我们可以看到远程仓库中还有一个 SSH 的地址，因此我们也可以使用 SSH 进行访问。 



接下来再往远程仓库 push 东西的时候使用 SSH 连接就不需要登录了。 



  

## 第 7 章 IDEA 集成 Git 

7.1 配置 Git 忽略文件 

1） Eclipse 特定文件 

2） IDEA 特定文件 

3） Maven 工程的 target 目录 

**问题 1:为什么要忽略他们？**
答： 与项目的实际功能无关，不参与服务器上部署运行。把它们忽略掉能够屏蔽 IDE 工具之
间的差异。
**问题 2：怎么忽略？**
1） 创建忽略规则文件 xxxx.ignore（前缀名随便起，建议是 git.ignore）
这个文件的存放位置原则上在哪里都可以，为了便于让~/.gitconfig 文件引用，建议也放在用
户家目录下
git.ignore 文件模版内容如下： 

```java
# Compiled class file
*.class
    
# Log file
*.log
# BlueJ files
*.ctxt
# Mobile Tools for Java (J2ME)
.mtj.tmp/
# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar
# virtual machine crash logs, see
http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*
.classpath
.project
.settings
target
.idea
*.iml    

```

2） 在.gitconfig 文件中引用忽略配置文件（此文件在 Windows 的家目录中） 

```java
[user]
	name = wqx
	email = 865684885@qq.com
[core] 
	excludesfile = "C:/Users/86568/git.config"  -- 引用忽略文件
```



### 7.2 定位 Git 程序 

```bash
D:\Enviroment\Git\bin\git.exe
```



### 7.3 初始化本地库 

选择要创建 Git 本地仓库的工程。 



### 7.4 添加到暂存区

右键点击项目选择 Git -> Add 将项目添加到暂存区。 



### 7.6 切换版本 



### 7.7 创建分支 

选择 Git， 在 Repository 里面，点击 Branches 按钮。 

在弹出的 Git Branches 框里， 点击 New Branch 按钮。 

填写分支名称，创建 hot-fix 分支。 

然后再 IDEA 的右下角看到 hot-fix，说明分支创建成功，并且当前已经切换成 hot-fix 分支 



### 7.8 切换分支

在 IDEA 窗口的右下角，切换到 master 分支。 

然后在 IDEA 窗口的右下角看到了 master，说明 master 分支切换成功。 



### 7.9 合并分支

​		在 IDEA 窗口的右下角，将 hot-fix 分支合并到当前 master 分支。 

​		如果代码没有冲突， 分支直接合并成功，分支合并成功以后，代码自动提交，无需手动提交本地库。 



### 7.10 解决冲突

​		如图所示，如果 master 分支和 hot-fix 分支都修改了代码，在合并分支的时候就会发生冲突。 

​		我们现在站在 master 分支上合并 hot-fix 分支，就会发生代码冲突。 

​		点击 Conflicts 框里的 Merge 按钮，进行手动合并代码。 

​		手动合并完代码以后，点击右下角的 Apply 按钮。 

​		代码冲突解决，自动提交本地库。 



## 第 8 章 IDEA 集成 GitHub

### 8.1 设置 GitHub 账号 

### 8.2 分享工程到 GitHub 

### 8.3 push 推送本地库到远程库

​		右键点击项目，可以将当前分支的内容 push 到 GitHub 的远程仓库中。 

​		注意： push 是将本地库代码推送到远程库，如果本地库代码跟远程库代码版本不一致，
push 的操作是会被拒绝的。也就是说， 要想 push 成功，一定要保证本地库的版本要比远程
库的版本高！ 因此一个成熟的程序员在动手改本地代码之前，一定会先检查下远程库跟本地
代码的区别！如果本地的代码版本已经落后，切记要先 pull 拉取一下远程库的代码，将本地
代码更新到最新以后，然后再修改，提交，推送！ 



### 8.4 pull 拉取远程库到本地库

​		右键点击项目，可以将远程仓库的内容 pull 到本地仓库。 

​		注意： pull 是拉取远端仓库代码到本地，如果远程库代码和本地库代码不一致，会自动
合并，如果自动合并失败，还会涉及到手动解决冲突的问题。 



### 8.5 clone 克隆远程库到本地 



为 clone 下来的项目创建一个工程，然后点击 Next。 



## 第 9 章 国内代码托管中心-码云 

### 9.1 简介

​		众所周知， GitHub 服务器在国外， 使用 GitHub 作为项目托管网站，如果网速不好的话，严重影响使用体验，甚至会出现登录不上的情况。针对这个情况， 大家也可以使用国内的项目托管网站-码云。 

​		码云是开源中国推出的基于 Git 的代码托管服务中心， 网址是 https://gitee.com/ ，使用
方式跟 GitHub 一样，而且它还是一个中文网站，如果你英文不是很好它是最好的选择。 









































创建远程库

```bash
https://github.com/weiqx/git-demo.git

weiqx   库
weiqx02 加入到  gitdemo库


https://github.com/weiqx/git-demo/invitations  -- 邀请函

----------------------------------
SSH
git@github.com:weiqx/git-demo.git

```

Github        (idea) 

```java

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  -- idea登录github口令  (token)
```

Gitee

```java
git-test  https 路径
https://gitee.com/weiqx/git-test.git

f7b0df5c279928ff60afdeb055acc4cc     -- token登录  私人令牌  只能用邮箱登录，邮箱又绑定不了
```











