---
title: Hexo 博客搭建教程
date: 2021-06-08 14:38:35
tags:
---
Hexo 是一个博客框架，项目语法是 Markdown，当然你也可以配置其他。

#### **安装 Hexo**

##### **1. 环境准备**

基础环境配置完善 (详见[基础物料](http://mp.weixin.qq.com/s?__biz=MzkxOTE2ODg4Mg==&mid=2247485552&idx=1&sn=1f106756384127c5c96ffcd5e474ff48&chksm=c1a77a6df6d0f37b26d1388b95a1e9fd1650cf4a2a68a986224e2d36c5bafcbcea35e6ff7d11&scene=21#wechat_redirect)) 可以输入一下命令进行环境 check 是否安装成功。

git --version

node -v

npm -v

##### **2. 安装**

```
npm install -g hexo-cli
```

##### **3. 初始化博客项目**

执行一下命令

hexo init xxx.github.io

cd xxx.github.io

项目结构如下：

```js
hiciciya.github.io
├── db.json
├── node_modules  // 依赖 
├── package.json // 应用程序信息
├── scaffolds  //模板文件夹 
│   ├── draft.md
│   ├── page.md
│   └── post.md
├── source // 资源文件夹 
│   └── _posts
├── themes //主题 博客风格
├── _config.landscape.yml
└── _config.yml //网站配置信息
```

##### **4. 本地运行项目**

npm run server

or

hexo -s

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTPHYQ0guwbKZwJOQPHF38Isibk4XzCibP6yhHYyibUBCM8zDMgvm7wNhibQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

项目本地就运行起来了！it'S WORK。

我们看到首页默认有一篇 HelloWord 的文章。我们来思考如何去控制这篇文章，在已生成目录中去找与 Helloword 内容相匹配的文件，发现** **/source/_posts/HelloWord ** **与我们看到的文章内容匹配。

```js
├── source
│   └── _posts
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsT1jrbmhCvHV92FsjSAnNTsDKDczVjqLo3Np1vvZwhdp0lJpBz0ShAPw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

##### **5. 尝试修改初始化的文章内容**

```
---title: 我的第一篇文章---
```

页面中文章名称跟着变化生效了。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTXPcNvibExpHeOxrjibL80BamyNchLq2XqtERibia3FcWDKWFs0ucBGdUPQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

得出的结论就是** **/source/_posts 下的** **md** **控制文章视图。

##### **6. 新建文章**

执行 hexo new MyWord

顺着我们刚才的逻辑 **/source/_posts** **应该增加一个 名为** **MyWord.md**  的文件。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTV8pfY8ONGic1ITepWibODKbxmib6X6sEI2gV2T43OeUqxGv1ZEyw9d9PQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

这样一篇文章就新建成功了！编辑文章内容，在 **MyWord.md** 可以随便来点内容。

```
---title: MyWorddate: 2021-06-03 13:49:16tags: ---### 我的世界很简单 简单到我每顿只吃大龙虾
```

页面同步更新哈

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTeibLGEPvYuxSgRialoU3t2KEwK1SzY8d5jyYI6sb5q3x65XJeibbIozjA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

恭喜第一篇博文发表成功！但是此刻仅是在本地哈。

### **3. 部署 Githubpages**

#### **部署思路**

* #### 本地代码变化
* #### 同步到远端仓库
* #### 客户端同步更新

能自动化实现该流程是理想状态，持续集成（CI）工具则是最优解。Hexo 官方推荐 Travis。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTsOMIZ8zcZF4LDaKiaRiacM5dOItSRDAxfzhqxtlibiao4R3cXyI7LCiaCOg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

#### **开始部署**

###### **1. Travis与github关联**

###### 点击** **https://www.travis-ci.com/** **进入** **Travis** 官网，右上角点击 `Sign in`按钮。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTyoict91AIcCUDKCsPAJiaERzJDuWOuu109hZzNPS2SdpLGclHY2do0eg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

进入 登录界面，点击 **SIGN IN WITH GITHUB** 按钮。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTR34UicFDgjh5wvRBiaAYQaUCJMpOA4cyNp6Jefwmiagj7aYEWfbpLK1jQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTnajgLJLMvu4utv0clTee7mV0sWTLOIL9CAFM7a8S5TTFHFXkLwI8Qg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

登录成功！

###### **2. Github 配置 Travis CI 权限**

点击当前页按钮 Activate all repositories using GitHub Apps

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTkia5QnlQJfSt4rYwvf6J7dLSz8BhoqOObicEqpgh89Mlox5SeHtoFSYQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

进入授权页面，点击 Approve Install

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTiaDvorvVQ60vUxLGRswHh1W2vCqfpeH7rrM9Oh3RtjmzAxTnoskib6OQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

初次关联的话，会重定向一些页面。如果有需要就选择绿色按钮，绿色代表同意，完成授权。

###### **3. 新建 Personal Access Token**

点击 github.com/settings/to… 点击 Generate new token

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTy7rUgQUAgJ1Y8RoCug2NgSKNnyNTDCs8N16nun1c3OnF4wBvibbW8GQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

键入 **Token** **名称，在** **Note** **项填入** **GH_TOKEN** **并只勾选** **repo** 的权限。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTKtIMsu4iaIibrXKYnR7dSfWShg4pSMHB3wiaMNZTNK5boJBcOdxycqatA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

左下角 **Generate token Token** **生成成功，复制新生成的** Token，如下图所示：

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTK0m7ODC7ZlibiajdU3RqZAaejuvQDyf9T0QN4l7MT4E9fiaC7M4cDMziaw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

###### **4. Travis CI 配置 Environment Variables 对应的项目仓库配置环境变量**

回到 **Travis CI** **主页，右侧选择选项目仓库，点击右上角** **More options** **下拉选择Settings，滚动至** Environment Variables。

新建环境变量 **Name** **为** **GH_Token VALUE，作为我们在** **GitHub** **生成的** Token。

ps：请确保 **DISPLAY VALUE IN BUILD LOG** **不被勾选，避免你的** Token 被泄漏。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTngLNoEXc9sSg8roDMnlkErjIFbV1jgD2qg4lOe6Iq3dia3VGErIh4ZA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTrA1o9S3m2l63jjm9nVxhiaKG00tFSIt3bicrllCh7So1iaPGrx4VII13A/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTrA1o9S3m2l63jjm9nVxhiaKG00tFSIt3bicrllCh7So1iaPGrx4VII13A/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

#### **项目配置CI**

##### **1. 新建一个 .travis.yml**

复制以下内容至 **.travis.yml** **文件

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTdTpYvRofLiaSmeP8fDX6OAnDuxVibAuCqZEV8ibN9BWmPdGXIPSfwGbVA/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)

##### **2. 提交本地代码至远端**

git add .

git commit -m "add travis config"

git push origin master

Travis CI 应该会自动开始运行，并将生成的文件推送到同一 **repository** **下的** **gh-pages** 分支下。

回到 **Travis CI** 官网，如下图所示，完成部署。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTMeHCia8E7Cz6Oia6GAVZqfI24tBs98mSsibywDspOicKTiafHU1icOIj8fCQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

#####

##### **3. 修改 GithubPages 部署分支**

回到 **Github** **对应项目主页，点击** **Settings。

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTNkU4KVZsjLgEobLu0LhfOUmUxYgtEdrMQtRkBEichiax6TZrteaM7xNQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

右侧侧边栏选择 **Pages Source，选择分支为** **gh-pages（默认部署为** **master** **分支) 点击** Save。

### **4. 浏览器 访问 xxxx.github.io**

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsT20vGbk5l3U5ibbxqJvO7jz4ibKz85tMc9KFOgrzWejSjKoZ8mpmFslRw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTzaZkrS4080fJaTz0aVFxYss18TEcabM2cnNwT8dkQQdmhyiaUjO3Rhg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

没有成功？？？我原本也是这样认为的，各种百度，吸取百家之长后，原来此时只是需要等 10 分钟或者 20 分钟。

稳住！！！

![图片](https://mmbiz.qpic.cn/mmbiz_png/nVsZGO5dvqmmRibzfMYDxOzwTftu4mtsTOuic6MYsu5g97PUl0RasMJCNIlzA0NvAg0dva97zp9KfskMJgOISlHQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

**done!!!**
