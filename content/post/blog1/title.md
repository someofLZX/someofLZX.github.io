---
title: 绘制差异代谢物impact pathway富集气泡图与Venn图
date: '2022-03-20'
summary: 代谢组;绘图
---

## 前言

基于已有的代谢组数据进行impact pathway富集气泡图与Venn图的绘制，用到的原始数据仅包括实验组和对照组的差异代谢物对应的KEGG号即可（或者差异代谢物名称也可），绘制成如下面这种效果图

<img src="https://s2.loli.net/2022/03/20/6L4bWtwnE572ZCr.png" alt="image-20220320221057563" style="zoom:80%;" />

<!--more-->

## Impact pathway富集气泡图的生成

### 代谢组数据分析

#### 使用MetaboAnalyst5.0分析

- 进入 [MetaboAnalyst5.0](https://dev.metaboanalyst.ca/MetaboAnalyst/home.xhtml) 点击主页中间的start直接开始

<img src="https://s2.loli.net/2022/03/20/sf6VIwPnRmLKid1.png" alt="image-20220320153445485" style="zoom:80%;" />

- 在内容选择界面选择`Pathway Analysis`

<img src="https://s2.loli.net/2022/03/20/TAYbJCvPr1M6OFp.png" alt="image-20220320153935489" style="zoom:80%;" />

- 进入之后选择`Compound List`，在输入框中粘贴差异代谢产物的KEGG号，并在`Input type`部分选择`KEGG ID`，这一步尽量直接用KEGG号，用差异代谢产物名称（相应选择`Compound Name`）话因为有别名的存在，即你手里的产物名（公司库的名字）和KEGG库里的不一致，导致在下一步可能还需要核对更换，而KEGG号则是唯一的

<img src="https://s2.loli.net/2022/03/20/vtu861LkqO7sjKI.png" alt="image-20220320154057709" style="zoom:50%;" />

- 等待录入匹配完成后会出现如下界面，可以看到都能匹配上则直接拉到最下面继续`Procced`（如果前一步被迫只能输产物名的话这一步还可以导出这个表格，得到对应的KEGG号，点击页面左下角的`Download result`）

<img src="https://s2.loli.net/2022/03/20/3l4b2UK7FeJqoHs.png" alt="image-20220320154733923" style="zoom:80%;" />

- 分析参数设置如果没有特别需求则选择默认设置就好，但是注意选择下面的`Pathway library`，根据实验涉及的物种进行选择，这里包含了常见的哺乳动物/鸟/与/昆虫/真菌/植物等，如果做的比较小众没有对应的则选择最相近的即可。比如我这里因为做的是奶牛则选择的`Bos taurus(cow)`。

<img src="https://s2.loli.net/2022/03/20/NkKtyhsoMUxQHmd.png" alt="image-20220320155021160" style="zoom:80%;" />

- 上一步继续后会生成如下结果，即我们需要的Impact pathway富集气泡图
  - 点击左边`Show gridline`之后`Update`可在图中显示网格线，便于更好的观察和认识结果
  - 左边气泡图的具体含义：横坐标轴是表示影响大小，圆圈越大代表对这条通路的影响越大；纵轴是-log10(p)，也就是p值可信度，圆圈越红代表可信度越高。每个圆圈对应的具体信息可查看下方表格
  - 点击图片下方的`Pathway Name`这一系列的超链接，回载页面有图出现这一堆差异代谢物具体hit到了该pathway那些部分，已经简化的代谢通路图

<img src="https://s2.loli.net/2022/03/20/9dQgJO4WqDscVIf.png" alt="image-20220320155546317" style="zoom:80%;" />



- 点击`Submit`之后会出现结果导出界面，建议直接选择打包下载也就是`Download.zip`到本地，方便调看查阅

<img src="https://s2.loli.net/2022/03/20/7WbkevEaZL5wyrg.png" alt="image-20220320160618757" style="zoom:80%;" />



## Impact pathway富集气泡图的加工

这里使用到的图片加工软件为Adobe Illustrator也就是AI

- 解压在MetaboAnalyst5.0得到的结果，选择`pathway_results.csv`文件打开

<img src="https://s2.loli.net/2022/03/20/Kjrt1oYyQnVmJPz.png" alt="image-20220320162904239" style="zoom:50%;" />

- 按`Raw p`升序排列，选取小于0.05的，K列的`Impact`也可以作为参考值，一般大于0.1认为有影响（如果富集到的代谢通路少可以不考虑），按p值大小插入A列拉动排序，记得B列留空

![image-20220320163352977](https://s2.loli.net/2022/03/20/gqiKtyrFpP5aVRB.png)

- 打开AI后新建大小合适的画布，将文件`path_view_1_dpi72`导入AI，在上面的表格中复制A-C列，粘贴至图片右边，并对应表格中的p值和impact值确定圆圈含义，标记序号一一匹配即可（下图的示例图用的另一个表格的）

<img src="https://s2.loli.net/2022/03/20/YwM8T1kU64ILmge.png" alt="image-20220320173415759" style="zoom:80%;" />

- 当impact pathway数量不多的时候也可以选择下面这种展示方式，更加直观

<img src="https://s2.loli.net/2022/03/20/ibvnSo87UejRlKW.png" alt="image-20220320210829028" style="zoom: 50%;" />



## Venn图的绘制

### Venn图数据整理

#### Excel初加工

- 将上面得到的每个比较组的impact pathway粘贴至新建的excel表格中，保存

<img src="https://s2.loli.net/2022/03/20/wBDjiyzl4OgaduP.png" alt="image-20220320215826572" style="zoom:67%;" />

### 使用在线Venn图工具分析

- 这里我用的是 [联川生物云平台](https://www.omicstudio.cn/tool)，进入主页注册账号后直接使用，目前免费。搜索Venn，选择如下普通的Venn图即可

<img src="https://s2.loli.net/2022/03/20/PTM3DB5KFYfGXlk.png" alt="image-20220320220126783" style="zoom: 33%;" />

- 进入页面后上传刚刚整理的excel表格，则会在右侧自动生成Venn图，对应的图片粗略细节调整可以参照下面箭头，比如调整圆圈颜色/标题位置/字体型号和大小等等

<img src="https://s2.loli.net/2022/03/20/eYt5EWGrZy8D3BL.png" alt="image-20220320220502646" style="zoom:67%;" />

- 点击右侧保存数据注意，选择对应的文件类型后，图片和表格是**分开保存**的，一定记得都要下载
- 保存到本地的图片可以利用AI进行细化加工



### 效果图展示

对比开头我之前画的版本，这次写教程演示如下，再补充图例等细节就是完整的figure了。选用哪种按需即可，毕竟美化加工方面因人而异且各有所长。

<img src="https://s2.loli.net/2022/03/20/j6aYR8N4BioKgzq.png" alt="image-20220320220859444" style="zoom:80%;" />