# 学员档案

## 基本信息

| 项目 | 内容 |
| --- | --- |
| GitHub 用户名 | senmumu2002 |
| 钱包地址（ETH钱包，用于发奖励） | 0xbF314fCC94E50515B22e68BE6afb08BC3D7cF8C5 |
| 联系方式（微信 / Telegram / Discord） | 微信：q153659802 |
| 是否加入学习交流群 | 是 |

> ⚠️ **钱包地址用于发放奖励，请务必认真填写并反复核对。** 因地址错误导致的奖励无法到账，主办方不承担责任。

## 学习笔记 / 心得

### github仓库操作流程

* 原作者：openbuildxyz/Avalanche-101-Bootcamp
* 你的 Fork：senmumu2002/Avalanche-101-Bootcamp
* 本地目录：Avalanche-101-Bootcamp

----------------------------------------------------

一、整个流程

                    GitHub
┌──────────────────────────────────────────┐
│                                          │
│  原作者仓库                               │
│  openbuildxyz/Avalanche-101-Bootcamp    │
│             │                            │
│             │ Fork                       │
│             ↓                            │
│  你的 GitHub 仓库                         │
│  senmumu2002/Avalanche-101-Bootcamp     │
│             ↑                            │
│             │ push                       │
└─────────────┼────────────────────────────┘
              │
            clone
              ↓
┌──────────────────────────────────────────┐
│              本地电脑                     │
│                                          │
│  Avalanche-101-Bootcamp                  │
│             │                            │
│          修改代码                         │
│             ↓                            │
│        git add / commit                  │
│             ↓                            │
│        git push origin main ──────────→ 你的 GitHub
│                                          │
│                                          │
│  git fetch upstream ←──────── 原作者仓库 │
│             ↓                            │
│     git merge upstream/main              │
│             ↓                            │
│       合并原作者 + 我的修改               │
│             ↓                            │
│     git push origin main ─────────────→ 你的 GitHub
└──────────────────────────────────────────┘

这里最重要的是理解两个名字：

origin
   ↓
你的 GitHub Fork
upstream
   ↓
原作者 GitHub 仓库

----------------------------------------------------

二、第一步：Fork 原作者仓库

打开原作者仓库：

⁠openbuildxyz/Avalanche-101-Bootcamp

点击 GitHub 页面右上角：

Fork

然后选择你的 GitHub 账号。

完成后，你会得到：

https://github.com/senmumu2002/Avalanche-101-Bootcamp

此时：

原作者
openbuildxyz/Avalanche-101-Bootcamp
        ↓ Fork
你的仓库
senmumu2002/Avalanche-101-Bootcamp

----------------------------------------------------

三、第二步：把你的 Fork 下载到本地

在你的 Fork 页面点击：

Code

选择 SSH，复制：

git@github.com:senmumu2002/Avalanche-101-Bootcamp.git

然后终端：

git clone git@github.com:senmumu2002/Avalanche-101-Bootcamp.git

进入项目：

cd Avalanche-101-Bootcamp

检查：

git status

检查远程仓库：

git remote -v

最开始通常会看到：

origin  git@github.com:senmumu2002/Avalanche-101-Bootcamp.git (fetch)
origin  git@github.com:senmumu2002/Avalanche-101-Bootcamp.git (push)

此时：

origin = 你的 GitHub 仓库

----------------------------------------------------

四、第三步：给原作者仓库添加 upstream

这是 Fork 工作流中非常重要的一步。

执行：

git remote add upstream git@github.com:openbuildxyz/Avalanche-101-Bootcamp.git

然后检查：

git remote -v

现在应该看到：

origin    git@github.com:senmumu2002/Avalanche-101-Bootcamp.git (fetch)
origin    git@github.com:senmumu2002/Avalanche-101-Bootcamp.git (push)
upstream  git@github.com:openbuildxyz/Avalanche-101-Bootcamp.git (fetch)
upstream  git@github.com:openbuildxyz/Avalanche-101-Bootcamp.git (push)

以后：

origin
  ↓
你的 GitHub
upstream
  ↓
原作者 GitHub

----------------------------------------------------

五、第四步：修改本地代码

例如你修改：

learn/senmumu2002/senmumu2002.md

修改完成后，先查看：

git status

可能看到：

Changes not staged for commit:
    modified: learn/senmumu2002/senmumu2002.md

查看具体修改：

git diff

这个命令非常有用。

它可以让你确认：

我到底改了什么？

----------------------------------------------------

六、第五步：把本地修改提交到 Git

首先：

git add learn/senmumu2002/senmumu2002.md

如果你希望添加所有修改：

git add .

然后查看：

git status

确认之后：

git commit -m "Update senmumu2002 profile"

提交之后：

git status

可能看到：

Your branch is ahead of 'origin/main' by 1 commit.

这意味着：

本地 main
   ↓
比 GitHub 的 main 多一个 commit

----------------------------------------------------

七、第六步：上传到你自己的 GitHub

执行：

git push origin main

这里一定注意：

git push origin main
          ↑
        你的 GitHub

因为：

origin = 你的仓库

所以这条命令的意思就是：

把本地 main 上传到我的 GitHub Fork。

上传后：

本地
  │
  │ git push origin main
  ↓
你的 GitHub

----------------------------------------------------

八、第七步：以后原作者更新了，先获取原作者代码

假设第二天：

openbuildxyz/Avalanche-101-Bootcamp

更新了。

这时候不要直接：

git pull

因为你的：

origin

是你的 GitHub Fork。

正确做法：

git fetch upstream

这个命令的意思：

从原作者仓库获取最新信息，但暂时不要修改我的当前代码。

可以查看：

git log --oneline --all --graph

----------------------------------------------------

九、第八步：把原作者更新合并到本地

执行：

git merge upstream/main

Git 会尝试：

原作者最新代码
        +
你自己的代码
        ↓
      合并
        ↓
本地 main

如果没有冲突，你可能看到：

Merge made by the 'ort' strategy.

这就表示：

合并成功。

----------------------------------------------------

十、如果出现 Conflict 怎么办？

例如：

git merge upstream/main

出现：

CONFLICT (content): Merge conflict in xxx.md

这并不意味着你的代码丢了。

Git 会在文件中显示：

<<<<<<< HEAD
你的代码
=======
原作者的代码
>>>>>>> upstream/main

你需要手动决定最终保留什么。

例如最终修改成：

你的代码 + 原作者的新代码

然后：

git add xxx.md

再：

git commit

如果有多个冲突文件：

git status

查看哪些文件发生冲突。

全部解决之后：

git add .
git commit

----------------------------------------------------

十一、第九步：把合并后的结果上传到自己的 GitHub

合并成功以后：

git push origin main

于是：

原作者仓库
      │
      │ git fetch upstream
      ↓
    本地
      │
      │ git merge upstream/main
      ↓
本地最新版本
      │
      │ git push origin main
      ↓
你的 GitHub Fork

这样你的 GitHub Fork 就同时包含：

原作者最新代码
+
你自己的修改

----------------------------------------------------

十二、以后每次同步的最简流程

如果你已经完成前面的配置，以后原作者更新，你只需要：

git fetch upstream
git merge upstream/main
git push origin main

也就是：

① 获取原作者更新
git fetch upstream
        ↓
② 合并原作者更新
git merge upstream/main
        ↓
③ 上传到自己的 GitHub
git push origin main

----------------------------------------------------

十三、推荐的完整安全流程

如果你准备修改自己的代码，然后又同步原作者，我建议养成下面这个习惯。

修改代码之前

git status

修改代码

编辑代码

查看修改

git diff

提交自己的修改

git add .
git commit -m "描述我的修改"

上传自己的修改

git push origin main

获取原作者更新

git fetch upstream

合并

git merge upstream/main

检查

git status

如果没有冲突

git push origin main

----------------------------------------------------

十四、把所有常用命令整理成一张表

操作    命令    作用
Clone    git clone URL    下载仓库
进入目录    cd 项目目录    进入项目
查看状态    git status    查看当前状态
查看远程    git remote -v    查看 origin/upstream
添加 upstream    git remote add upstream URL    连接原作者仓库
查看修改    git diff    查看代码修改
添加文件    git add 文件    将修改加入暂存区
添加全部    git add .    添加所有修改
提交    git commit -m "xxx"    创建本地 commit
上传自己仓库    git push origin main    上传到你的 GitHub
获取原作者    git fetch upstream    获取原作者最新代码
合并原作者    git merge upstream/main    合并到本地
查看历史    git log --oneline --graph    查看提交历史

----------------------------------------------------

十五、你现在这个仓库对应的实际命令

你的情况已经配置好了，所以以后实际上就是：

cd Avalanche-101-Bootcamp
# 查看状态
git status
# 修改代码
# ...
# 查看修改
git diff
# 保存自己的修改
git add .
git commit -m "我的修改说明"
# 上传自己的 GitHub
git push origin main
# ==========================
# 原作者更新之后
# ==========================
# 获取原作者最新代码
git fetch upstream
# 合并原作者
git merge upstream/main
# 如果没有冲突
git push origin main

其中最值得记住的就是这三个：

git fetch upstream
git merge upstream/main
git push origin main

可以把它记成：

从原作者拿 → 合并到我本地 → 推回我的 GitHub

而你以后看到：

origin

就想：

我的 GitHub

看到：

upstream

就想：

原作者 GitHub

这就是整个 Fork 协作流程的核心。

### 第一章：Avalanche 从零入门

官方网址：core.app
索取测试空投：
tools -> Avalanche testnet Faucet -> Fuji (C-Chain) -> AVAX -> 输入钱包地址后人机身份验证（优惠券代码avalanche-academy） -> 请求

### 第二章：Vibe Coding 开发第一个 DApp

