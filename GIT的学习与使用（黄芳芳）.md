# GIT的学习与使用
-------
***学习背景***：什么，git是啥，一无所知<br>
***学习目录***：<a name=back>(点击即可跳转)</a><br><a href=#t1>一、Git简介</a>💡💡
<br><a href=#t2>二、Git原理</a>💡💡
<br><a href=#t3>三、远程仓库</a>💡💡
<br><a href=#t4>四、分支管理</a>💡💡
<br>

--------
## <a name=t1>一、Git简介</a>💡💡
<a href=#back>(返回目录）</a>
```
1.git是目前世界上最先进的分布式版本控制器
2.版本控制器：（我的理解）此版本是你所写文件的版本，每次修改便会产生一个新“版本”，
版本控制器可以监测到版本之间的差异，记录每次修改的数据，还可以让其他人协作编辑
```
#### 1.Git的诞生✨

- *(此文段摘自廖雪峰的官方网站，这段故事很有趣✨)*

- Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？

  事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！

  你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。

  不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。

  安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。

  Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：

  Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。

  Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。

  历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。
#### 2.集中式和分布式（版本控制器）✨
|        |   网络   |    版本库位置    | 安全性 |
| :----: | :------: | :--------------: | :----: |
| 集中式 |  需联网  |    中央服务器    |   差   |
| 分布式 | 不需联网 | 每人电脑都可以有 |   好   |

#### 3.下载git、创建版本库✨

**git配置**：查看配置git config -l   & git/ect/gitconfig

				     用户信息查看 git config --global user .name  "..." .email "..."

----------
## <a name=t2>二、Git原理</a>💡💡
<a href=#back>(返回目录）</a>
#### 1.Git工作原理✨

* git有三个工作区域：工作目录(workspace)、暂存区(stage/index)、资源库(local repositiry)，如果加上远程git仓库(romote repository)就可以算四个区，四个区之间转换关系如下：

![7](https://github.com/SnowSPomPom/Tasks/blob/main/image/7.jpg)

  （其中暂存区是隐藏目录）

  详情见[Tasks/Git的使用2（实操）](https://github.com/SnowSPomPom/Tasks/blob/main/Git的使用2（实操）.md)

-----------
## <a name=t3>三、远程仓库</a>💡💡
<a href=#back>(返回目录）</a>
```
首先添加一个SSH密钥
```

#### 1.添加远程仓库✨

* 复制SSH框下面的地址

  * 在git bash中输入` git remote add 名称 shh地址`

  * `git remote -v`可以一览远程仓库

* 建立推送桥梁

  * 在要建立联系的本地目录下运行git bush，输入命令`git remote add "桥梁名称""仓库地址"`
  
* 推送文件

  * 输入命令`git push "主机名称""本地分支":"远程分支"`

#### 2.从远程仓库克隆✨

+ 准备好远程库及其地址（.git）

+ 在要克隆过来的本地目录下运行git bash，输入命令`git clone "远程库地址"`即可完成克隆

--------------
## <a name=t4>四、分支管理</a>💡💡
<a href=#back>(返回目录）</a>
#### 1. 创建与合并分支✨

* **创建与合并分支的原理**
  * *（廖雪峰网站上的解释真的很清晰，就复制过来了）*
  * **一开始的时候**，`master`分支是一条线，Git用`master`指向最新的提交，再用`HEAD`指向`master`，就能确定当前分支，以及当前分支的提交点： 
  
  ![1.1](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/1.1.png)
  
    每次提交，`master`分支都会向前移动一步，这样，随着你不断提交，`master`分支的线也越来越长。
  * **当我们创建新的分支**，例如`dev`时，Git新建了一个指针叫`dev`，指向`master`相同的提交，再把`HEAD`指向`dev`，就表示当前分支在`dev`上：  
  
  ![1.2](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/1.2.png)
  
    你看，Git创建一个分支很快，因为除了增加一个`dev`指针，改改`HEAD`的指向，工作区的文件都没有任何变化！
  * **不过**，从现在开始，对工作区的修改和提交就是针对`dev`分支了，比如新提交一次后，`dev`指针往前移动一步，而`master`指针不变：
  
   ![1.3](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/1.3.png)
  
  * **假如我们在`dev`上的工作完成了**，就可以把`dev`合并到`master`上。Git怎么合并呢？最简单的方法，就是直接把`master`指向`dev`的当前提交，就完成了合并： 
  
   ![1.4](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/1.4.png)
  
    所以Git合并分支也很快！就改改指针，工作区内容也不变！
  * **合并完分支后**，甚至可以删除`dev`分支。删除`dev`分支就是把`dev`指针给删掉，删掉后，我们就剩下了一条`master`分支：
   ![1.5](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/1.5.png)<br>
* **2.创建与合并分支实操**✨
  * **首先**，创建`SnowsP`分支,然后切换到该分支（`-b`表示创建并切换）<br>
   ![2.1](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/2.1.png)<br>
  * **然后**，用`git branch`命令查看当前分支（当前分支前会标一个*号）<br>
   ![1.2](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/2.2.png)<br>
  * **然后**，我们可以在分支上正常提交，如我们提交修改一点的“hello.md"，提交<br>
   ![1.2](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/2.3.png)<br>
  * **现在**，分支工作完成，我们可以切换会`master`分支<br>
   ![1.2](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/2.4.png)<br>
  * **切换**回`master`分支后，再查看一个`hello.md`文件，刚才添加的内容不见了！因为那个提交是在`snowsp`分支上，而`master`分支此刻的提交点并没有变<br>
  * **现在**我们合并工作成果<br>
    ![1.2](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/2.5.png) <br>
  * **合并完**后就可以方向删掉分支了<br>
   ![1.2](https://github.com/SnowSPomPom/Tasks/blob/main/image/git%E5%88%86%E6%94%AF/2.6.png)<br>
  * 因为创建、合并和删除分支非常快，所以Git鼓励你使用分支完成某个任务，合并后再删掉分支，这和直接在`master`分支上工作效果是一样的，但过程更安全。
-------
 **参考资料**：廖雪峰网站、google、B站某git教程



​    
