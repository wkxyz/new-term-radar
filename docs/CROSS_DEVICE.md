# 新词研究工具：Windows / macOS 接续

## 第一次在新电脑打开

仓库：https://github.com/wkxyz/new-term-radar

本次设置保存在 `chore/cross-device-20261016`。初次取得本次交付：

```sh
git clone --branch chore/cross-device-20261016 https://github.com/wkxyz/new-term-radar.git
cd new-term-radar
```

若该分支已合并并删除，正常克隆默认分支即可，不再继续旧分支。已有目录先检查未提交改动；不要用新克隆覆盖它。

准备环境：需要 Python 3.10+。核心使用标准库；测试及可选功能依赖按 README.zh-CN.md 安装。

## 本地运行／编辑入口

Windows PowerShell：

```
$env:PYTHONUTF8='1'
py -3 -m radar --help
```

macOS：

```
python3 -m radar --help
```

config.json、令牌、数据库和历史报告留在各自受控环境。真正采集和发邮件可能调用外部服务，应先检查授权、配置与用量。本次不启动采集、不启用 Actions 定时任务。现有公开 fork 的可见性维持原设置。

## 按实际修改选择检查

Windows：

```
$env:PYTHONUTF8='1'
py -3 -m pytest -q tests
```

macOS：

```
python3 -m pytest -q tests
```

仅修改交接文档时检查引用、配置及 `git diff --check`；运行功能检查时在 STATUS.md 记录真实命令和结果。不要为了查看交接资料运行生产部署、数据库迁移或付费任务。

## 每次换电脑

1. 离开前停下仍在写文件的 AI／脚本，更新 [STATUS.md](../STATUS.md)，提交并推送当前任务分支，确认远端收到提交。
2. 到另一台电脑先检查 `git status`。工作区干净后 `git fetch origin`；续接同一任务就切换到对应任务分支，再执行 `git pull --ff-only`。
3. 新任务从最新默认分支另建任务分支；同一任务分支避免两个设备同时写入。遇到差异先对比，不强推或重置。
4. 打开本项目文件夹作为 Codex 项目，让 AI 先读 README、AGENTS、STATUS 和项目交接资料。聊天同步不代替文件同步。
5. 代码推送、预览、生产发布分别记录；既有生产发布要求和明确授权保持有效。

## 其他项目记录

- [README.zh-CN.md](../README.zh-CN.md)
