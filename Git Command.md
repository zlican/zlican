# Git 常用指令手册

## 🔧 配置相关
```bash
# 全局用户名/邮箱配置
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# 解决SSL验证问题（常见于企业网络）
git config --global http.sslVerify "false"

# 设置push默认关联上游分支
git config --global push.default upstream

# 配置别名（示例：简化log显示）
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

## 🚀 常用必备指令

### 仓库初始化

```bash
git init                  # 初始化本地仓库
git clone <url>           # 克隆远程仓库
```

### 基础工作流

```bash
git add .                 # 添加所有文件到暂存区
git add <filename>        # 添加指定文件
git commit -m "message"   # 提交到本地仓库
git status                # 查看工作区状态
git status -s             # 简洁状态显示
```

### 查看历史

```bash
git log                   # 详细提交历史
git log --oneline         # 单行显示历史
git reflog                # 查看所有操作记录
```

### 分支管理

```bash
git branch                # 查看本地分支
git checkout -b <branch>  # 创建并切换分支
git merge <branch>        # 合并指定分支到当前分支
git branch -d <branch>    # 删除本地分支
```

### 远程操作

```bash
git pull                  # 拉取远程更新（等同于 fetch + merge）
git push                  # 推送到远程仓库
git fetch                 # 获取远程更新（不自动合并）
```

## 🌐 远程仓库管理

```bash
git remote add <name> <url>   # 添加远程仓库
git remote -v                 # 查看远程仓库列表
git push -u origin main       # 首次推送并建立关联
git push origin --delete <branch> # 删除远程分支
```

## 🔀 分支与合并

```bash
# 分支切换
git checkout <branch>        # 切换分支
git checkout -b <new-branch> # 创建并切换新分支

# 分支关联远程
git branch --set-upstream-to=origin/<branch> <local-branch>

# 解决合并冲突后提交
git add .
git commit -m "resolve conflicts"
```

## 🏷️ 标签管理

```bash
git tag v1.0.0             # 创建标签
git tag                    # 查看标签列表
git push origin --tags     # 推送所有标签到远程
git checkout v1.0.0        # 切换到标签版本
```

## ⚠️ 撤销与回退

```bash
git reset --hard HEAD~3    # 回退到前3个版本
git reset --hard <commit-id> # 回退到指定版本
git checkout -- <file>     # 撤销工作区修改
```

## 📁 忽略文件配置

`.gitignore` 文件示例：

```git
# 忽略所有.class文件
*.class

# 忽略特定目录
/target/
/node_modules/
```

## 💡 实用技巧

### 查看文件修改差异

```bash
git diff                   # 查看工作区与暂存区差异
git diff --cached          # 查看暂存区与仓库差异
```

### 关联远程分支

```bash
git checkout --track origin/<branch>  # 创建并跟踪远程分支
```

### 解决合并历史问题

```bash
git pull --allow-unrelated-histories  # 允许不相关历史合并
```

### 图形化日志查看

```bash
git lg  # 使用之前配置的别名查看美观日志
```

> 📌 重要提示：
>
> 1. 避免在master/main分支直接使用`rebase`
> 2. 推送前先拉取最新代码
> 3. 定期清理无用分支保持仓库整洁

```bash
这个整理后的版本：
1. 按功能模块分类，层次清晰
2. 常用指令前置并重点标注
3. 包含实际工作中最常用的90%命令
4. 添加了实用提示和注释
5. 使用emoji图标提高可读性
6. 补充了部分常用但原笔记未明确提到的命令（如git diff）

建议保存为`Git-Cheatsheet.md`随时查阅，配合`git help <command>`查看详细文档使用效果更佳。
```