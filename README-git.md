# Actions-OpenWrt 项目导入 下载 及合并

Actions-OpenWrt 原始的项目地址：[https://github.com/Speechless22/Actions-OpenWrt](https://github.com/Speechless22/Actions-OpenWrt)
在github上导入项目作为私有仓库, 并在本地用如下命令克隆项目:

```bash
git clone https://github.com/xg427/Actions-OpenWrt.git
```

## 1.将导入的原始GitHub项目作为远程仓库

### 1.1. 检查当前远程仓库配置

首先，检查当前项目的远程仓库配置，看看是否已经设置了远程仓库。

```bash
git remote -v
```

显示结果如下:

```bash
origin  https://github.com/xg427/Actions-OpenWrt.git (fetch)
origin  https://github.com/xg427/Actions-OpenWrt.git (push)
```

如果当前还没有远程仓库或者你想添加另一个远程仓库，请继续下一步。

### 1.2. 添加远程仓库

假设你想将原始的GitHub项目添加为一个远程仓库（可以为它命名为upstream），你可以使用以下命令：

```bash
git remote add upstream https://github.com/Speechless22/Actions-OpenWrt.git
```

- upstream 是远程仓库的名字，你可以用其他名字代替它。
- git remote add upstream https://github.com/Speechless22/Actions-OpenWrt.git
  https://github.com/Speechless22/Actions-OpenWrt.git 是你导入的项目的原始的GitHub仓库地址。

### 1.3. 验证远程仓库添加成功

添加完成后，你可以再次检查远程仓库配置，确保远程仓库已正确添加：

```bash
git remote -v
```

显示结果如下:

```code
origin     https://github.com/xg427/Actions-OpenWrt.git (fetch)
origin     https://github.com/xg427/Actions-OpenWrt.git (push)
upstream   https://github.com/Speechless22/Actions-OpenWrt.git (fetch)
upstream   https://github.com/Speechless22/Actions-OpenWrt.git (push)
```

这时你已经能看到新的远程仓库upstream的URL。

### 1.4. 从远程仓库获取更新（可选）

如果你想从upstream仓库中获取最新的代码更新，你可以使用以下命令：

```bash
git fetch upstream
```

从全部远程仓库中获取最新的代码更新，你可以使用以下命令：

```bash
git fetch --all
```

## 2. 合并代码

从upstream仓库中获取更新后(见1.4)，你可以使用以下命令将代码合并到你的本地分支：

### 2.1 切换到你想合并更新的本地分支

确保你在想要合并更新的本地分支上。例如，如果你想在main分支上合并更新：

```bash
git checkout main
```

### 2.2. 合并upstream分支的更新到本地分支

使用以下命令将upstream仓库的某个分支（例如main）合并到你的本地分支：

```bash
git merge upstream/main
```

### 2.3. 解决冲突（如果有）

如果在合并过程中有冲突，Git会提示你解决冲突。你可以按照提示修改冲突的文件，然后使用以下命令标记冲突已解决：

```bash
git add <file>
```

其中，file 是冲突的文件名, 完成所有冲突的解决后，提交合并：

```bash
git commit
```

### 2.4. 推送合并后的代码到远程仓库（可选）

如果你希望将合并后的代码推送到你的远程仓库，可以使用以下命令：

```bash
git push origin main
```

其中，origin 是你的远程仓库，main 是你要推送的分支名称。

### 总结

通过以上步骤，你已经成功地将原始GitHub项目作为远程仓库添加到了你的本地项目中，并可以方便地进行代码同步和推送操作。

## 3.项目运行

### 3.1 安装依赖项

在项目根目录下，使用 npm 安装依赖项

```bash
npm install
```

### 3.2 测试

vitest 是一个用于 JavaScript 和 TypeScript 项目的测试框架，类似于 Jest。

运行全部测试

```bash
npm run test
```

运行一个测试

```bash
vitest run tests/indicators.test
```

如果你想更精确地运行特定测试，可以结合 -t 选项指定测试名称的一部分，例如：

```bash
vitest run example.test.js -t "测试名称的一部分"
node .\examples\AllPrivateIndicators.js zzzxr5logbv1tx3b5312u5q62k61zevc v3:gyS8YF2tYugEAQ1fDeaynPrWu/RDUjz3EhCICgeAxlg=
```
