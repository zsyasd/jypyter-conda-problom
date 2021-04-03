~~终于给我搞定了~~

实验室服务器只给我们提供了一个jupyter lab的模式登陆，那么我们使用的话都需要自己在上面配置东西。问题是这个服务器设置比较搞笑，他会给我们一个文件夹：「myname」，这个文件夹下安装东西 容量是不受限的，就你随便折腾。但是，他默认kernel链接的python路径和terminal路径却是根目录下面的。所以我装了个conda再加了n个package，他就跟我说我用了超过10个g，要么自己改好要么他帮我重制。

so···那我直接让他给我重制了，然后重新配置。

### 那重新配置首先第一步：下载conda

这一步不用怎么说，网上教程一抓一大把，或者直接上官网看一下就行，墙内的小伙伴可能需要用国内镜像。不过由于我安装包一直都在服务器上所以我直接安装了。

### 安装conda

这个要注意，因为他在后面会问你是否安装在conda默认路径下。要注意在这个情况下要注意输入你自己想要的安装路径

然后安装完之后别忘了bash：

```
export PATH="/home/username/anaconda/bin:$PATH"
```

然后安装成功

### 重头戏，指定kernel

首先，我们可以先在terminal和kernel下面分别输入：

```python
import sys
print(sys.executable)
```

在上面bash之后，我们terminal的环境路径已经被切换到conda下面了，所以我们会发现默认kernel和terminal下面的路径是不一样的。这实际上会很致命，因为我第一次意识到这个问题是在打天池一个比赛的时候发现我kernel下面很多包没有，但是同样的我在terminal下面conda install他会跟我说已经安装了。然后我才意识到这个问题。

然后我们在terminal下输入这个内容：

```terminal
conda install ipykernel //插件安装

python -m ipykernel install --name Name //这个就是新建一个kernel指向当前的目录。注意大写那个name指的是你自己要取的名字。
```

ok，搞定 大功告成。

开 始 M L

享 受 做 AI 的 快 乐