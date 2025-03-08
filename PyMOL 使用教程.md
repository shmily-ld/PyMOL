# PyMOL 使用教程

***Written by 22网安4班——罗丹***

## PyMOL 安装

### 方法 1

如果有下面三个 .whl 文件的话可以离线安装（可以使用清华源的镜像下载，链接：[Simple Index (tsinghua.edu.cn)](https://pypi.tuna.tsinghua.edu.cn/simple/)）

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151212225.png" alt="PixPin_2025-01-15_12-12-21" style="zoom:80%;" />

下载的时候要注意自己 python 的版本和操作系统的架构，可以使用如下命令查看电脑适配 Wheel 文件支持的架构和 Python 版本

```shell
pip debug --verbose
```

![PixPin_2025-01-15_12-20-26](https://gitee.com/faith22/typora/raw/master/img/202501151220323.png)



### 方法 2

如果有 anaconda 的话，可以直接用 conda 安装，简单方便，懒人必备

```shell
conda install conda-forge::pymol-open-source
```

下载完之后，可以直接在终端输入 pymol 进入界面

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151236983.png" alt="PixPin_2025-01-15_12-36-15" style="zoom:80%;" />



## PyMOL 基本使用方法

### 下载 PDB 文件

#### RCSB PDB数据库下载

一般 PDB 文件需要从 RCSB PDB 中下载（链接：[RCSB PDB: Homepage](https://www.rcsb.org/)）

这里以 PDB ID 为 6DVM 的蛋白质为例，下载它对应的 PDB 文件

![PixPin_2025-01-15_12-52-12](https://gitee.com/faith22/typora/raw/master/img/202501151252984.png)



#### PyMOL下载

也可以用 PyMOL 下载 PDB 文件（不推荐，有时候会有 Bug ）

下载方法：

```shell
打开 PyMOL GUI 界面 -> 点击 file -> 点击 Get PDB File -> 输入 PDB ID 即可 Download
```



### 导入 PDB 文件

打开 PyMOL GUI 界面，点击 File 下的 open file，选择刚刚下载的PDB文件即可

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151300978.png" alt="PixPin_2025-01-15_13-00-05" style="zoom: 50%;" />

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151302922.png" alt="PixPin_2025-01-15_13-02-13" style="zoom:50%;" />

如果之前已经打开了别的 PDB 文件进行操作，无需重新启动 PyMOL，可以点击 File -> Reinitialize-> Everything 就可以重置初始化页面

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151304711.png" alt="PixPin_2025-01-15_13-04-11" style="zoom:50%;" />



### 可视化教程

通过上一步导入 PDB 文件之后，可以看到如下页面：

![PixPin_2025-01-15_13-07-05](https://gitee.com/faith22/typora/raw/master/img/202501151307078.png)



#### 显示序列

我们点击界面右下角的 S 就可以显示出 sequence 序列信息

![PixPin_2025-01-15_13-12-49](https://gitee.com/faith22/typora/raw/master/img/202501151312536.png)



#### 消除水分子

图中有很多红点，表示的是水分子，在界面右边点击 ‘A’（Action）下的 Remove waters

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151316741.png" alt="PixPin_2025-01-15_13-16-29" style="zoom: 50%;" />

消除水分子之后可以看到没有红色的点了

![PixPin_2025-01-15_13-17-34](https://gitee.com/faith22/typora/raw/master/img/202501151317152.png)



#### 消除配体

按住 ctrl 键，点击 sequence 中的配体

![PixPin_2025-01-15_14-58-59](https://gitee.com/faith22/typora/raw/master/img/202501151459988.png)

可以看到选中了所有配体，点击右边的 sale 中的 ‘A’(Action)，选择 Remove atom，即可消除，这里为了后面方便演示，我们仅保留了一个配体和一个蛋白质链

![PixPin_2025-01-15_15-05-00](https://gitee.com/faith22/typora/raw/master/img/202501151505188.png)



#### 找出相互作用的残基

PyMOL 提供找出和配体发生作用的残基功能，首先在图中选中配体

选中之后，右边这个 (sale) 也就是 selection，表示当前选择的部位，点击下图所示的位置

![PixPin_2025-01-15_15-10-22](https://gitee.com/faith22/typora/raw/master/img/202501151510144.png)

就可以看到黄色的虚线，黄色的虚线连接的就是配体和相互作用的残基

![PixPin_2025-01-15_15-11-55](https://gitee.com/faith22/typora/raw/master/img/202501151512264.png)

目前残基并不能看到，为了更加详细的展示，将蛋白质的可视化形式从 cartoon 转变为 sticks，不过在这之前我们需要先将配体从蛋白质中分离出来

选中图中的配体，点击sale -> ‘A’ -> extract object

![PixPin_2025-01-15_15-16-39](https://gitee.com/faith22/typora/raw/master/img/202501151516582.png)

可以看到已经分离了

我们再选中蛋白质6dvm，将其用 sticks 表现出来：

![PixPin_2025-01-15_15-18-47](https://gitee.com/faith22/typora/raw/master/img/202501151518952.png)

![PixPin_2025-01-15_15-19-39](https://gitee.com/faith22/typora/raw/master/img/202501151519933.png)

这样就可以看到相连的是什么残基了



#### 配色

获得相互作用的残基之后，为了更好的方便截图，我们可以对其进行配色

首先将配体的颜色调整一下，以方便和其他进行区别，选中配体，点击 sale 的 color 选项，我们让它变成黄色以突出显示

![PixPin_2025-01-15_15-22-18](https://gitee.com/faith22/typora/raw/master/img/202501151522127.png)

![PixPin_2025-01-15_15-23-01](https://gitee.com/faith22/typora/raw/master/img/202501151523899.png)

现在我们可以很方便的找出这个配体连接的残基了，还记得之前黄色的虚线嘛，没错，我们根据这个虚线，选中相连的残基（为了方便选中，也可以按照 ctrl + 鼠标滚动放大放小图，拖动鼠标更换视角）

![PixPin_2025-01-15_15-27-20](https://gitee.com/faith22/typora/raw/master/img/202501151527886.png)

目前是已经选中了，接下来凸显这个残基

首先将整个蛋白质的 sticks 隐藏起来，点击 6dvm 的 H (hidden) -> sticks，再点击它的 color ，选择grey80

![PixPin_2025-01-15_15-29-58](https://gitee.com/faith22/typora/raw/master/img/202501151530912.png)

我们之前已经选中了相互作用的残基，因为我们点击 sale -> s -> sticks，展示出来，并修改他的配色，我比较喜欢 by element中的蓝白配色：

![PixPin_2025-01-15_15-32-28](https://gitee.com/faith22/typora/raw/master/img/202501151532125.png)

修改配色的颜色：选中配体，点击color给他进行配色，我比较喜欢将他变为绿色

![PixPin_2025-01-15_15-34-00](https://gitee.com/faith22/typora/raw/master/img/202501151534673.png)

论文里面图片一般需要白色，所以将背景调为白色：

![PixPin_2025-01-15_15-35-43](https://gitee.com/faith22/typora/raw/master/img/202501151535672.png)

同时呢，给蛋白质调成透明色：

![PixPin_2025-01-15_15-37-45](https://gitee.com/faith22/typora/raw/master/img/202501151537593.png)

最后，效果如下所示：

![PixPin_2025-01-15_15-38-19](https://gitee.com/faith22/typora/raw/master/img/202501151538361.png)



#### 显示残基 lable

为了更加细节的展示，我们一般显示残基的名字，也就是它的标签 lable

选中残基，点击 sale -> L -> residues

![PixPin_2025-01-15_15-40-50](https://gitee.com/faith22/typora/raw/master/img/202501151540813.png)

目前来说，字体很小，而且位置也不太好看

##### 调字体

PyMOL setting 中 Label可以设置字体大小，字体，颜色

![PixPin_2025-01-15_15-42-55](https://gitee.com/faith22/typora/raw/master/img/202501151542977.png)

为了方便后面调整字体的位置，我们将字体先变大一点，位置调好后可以再变小

![PixPin_2025-01-15_15-44-49](https://gitee.com/faith22/typora/raw/master/img/202501151544886.png)

##### 调整 Label 的位置

点击右下角的 Viewing，即可变为 Editing

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151546333.png" alt="PixPin_2025-01-15_15-46-15" style="zoom: 80%;" />

变为 Editing 之后，我们可以按住 ctrl，鼠标拖动 Label 的位置了，**注意如果不小心拖动到了蛋白质或者配体，可以ctrl + Z 撤回**，我们拖动到合适的位置，然后将字体适当的进行变小，调整视角：

![PixPin_2025-01-15_15-49-25](https://gitee.com/faith22/typora/raw/master/img/202501151549585.png)



#### 显示键的距离

有时候需要显示相互作用之间的距离，也就是图中黄色的虚线的长度，一般单位是Å（埃米）

选中右边的 sale_polar_conts，可以调这个虚线的颜色等等，点击 S 中的 Labels就可以展示距离

![PixPin_2025-01-15_16-12-41](https://gitee.com/faith22/typora/raw/master/img/202501151612807.png)



### 导出图片

点击 PyMOL 界面的 File -> Export Image As -> PNG，选择透明背景

![PixPin_2025-01-15_16-14-41](https://gitee.com/faith22/typora/raw/master/img/202501151614932.png)

可能需要等几秒，最后导出来如下：

![PixPin_2025-01-15_16-16-22](https://gitee.com/faith22/typora/raw/master/img/202501151616386.png)

就可以放到论文中咯：

![PixPin_2025-01-15_16-17-25](https://gitee.com/faith22/typora/raw/master/img/202501151617810.png)





## 分子对接可视化

如果我们没有蛋白质和配体的复合物 PDB 文件，则可以利用分子对接得到他们的复合物 PDB 文件，比如以上面PDB ID 为 6dvm 的蛋白质为例，要得到它和药物 Oseltamivir 的可视化图

### 数据处理

首先，要将 6dvm 这个PDB 中的小分子都去掉（前面有教程），如图所示

![PixPin_2025-01-15_16-27-17](https://gitee.com/faith22/typora/raw/master/img/202501151627833.png)

将结构保存为 PDB 文件，点击 File -> Save Molecule，选择保存类型为 .pdb 就 OK 了

<img src="https://gitee.com/faith22/typora/raw/master/img/202501151629920.png" alt="PixPin_2025-01-15_16-29-13" style="zoom:50%;" />

药物的话，可以在 DrugBank 里面下载对应的文件，有mol、mol2、sdf文件格式，根据要去下载就好了

![PixPin_2025-01-15_16-31-16](https://gitee.com/faith22/typora/raw/master/img/202501151631736.png)



### 分子对接

推荐几个常用的分子对接软件：AutoDock、DeepMice、3D-DOCK、CB-DOCK2

将分子对接的结构通过 PyMOL 可视化即可