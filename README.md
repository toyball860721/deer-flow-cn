# 🦌 DeerFlow - 2.0 中文文档

> 🚀 **Super Agent Harness** — 让 Agent 可以完成几乎任何事情
> 
> 📦 原版项目：[bytedance/deer-flow](https://github.com/bytedance/deer-flow) (GitHub Trending #1)
> 
> 🤖 字节跳动开源 | 🔥 2026 年 2 月 28 日登上 GitHub Trending 第 1 名

[![Python](https://img.shields.io/badge/Python-3.12%2B-3776AB?logo=python&logoColor=white)](./backend/pyproject.toml)
[![Node.js](https://img.shields.io/badge/Node.js-22%2B-339933?logo=node.js&logoColor=white)](./Makefile)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/toyball860721/deer-flow-cn?style=social)](https://github.com/toyball860721/deer-flow-cn)
[![GitHub Sponsors](https://img.shields.io/badge/GitHub_Sponsors-Support_EA42F5?logo=github)](https://github.com/sponsors/toyball860721)

**PROD-016** | Long-tail Track Product | v2.0.0 | 🆓 免费文档

---

## 📑 目录

- [一句话安装](#一句话交给-coding-agent-安装)
- [快速开始](#快速开始)
- [核心特性](#核心特性)
- [从 Deep Research 到 Super Agent Harness](#从-deep-research-到-super-agent-harness)
- [推荐模型](#推荐模型)
- [常见问题](#常见问题)
- [作者与其他项目](#作者与其他项目)

---

## 一句话交给 Coding Agent 安装

如果你在用 Claude Code、Codex、Cursor、Windsurf 或其他 coding agent，可以直接把下面这句话发给它：

```text
如果还没 clone DeerFlow，就先 clone，然后按照 https://raw.githubusercontent.com/bytedance/deer-flow/main/Install.md 把它的本地开发环境初始化好
```

这条提示词是给 coding agent 用的。它会在需要时先 clone 仓库，优先选择 Docker，完成初始化，并在结束时告诉你下一条启动命令，以及还缺哪些配置需要你补充。

![Demo](./docs/demo.gif)

---

## 快速开始

### 配置

1. **克隆 DeerFlow 仓库**
   ```bash
   git clone https://github.com/bytedance/deer-flow.git
   cd deer-flow
   ```

2. **生成本地配置文件**
   ```bash
   make config
   ```

3. **配置你要使用的模型** - 编辑 `config.yaml`

4. **为已配置的模型设置 API key** - 编辑 `.env` 文件

### 运行应用

#### 方式一：Docker（推荐）

```bash
make docker-init    # 拉取 sandbox 镜像
make docker-start   # 启动服务
```

访问地址：http://localhost:2026

#### 方式二：本地开发

```bash
make check    # 检查依赖环境
make install  # 安装依赖
make dev      # 启动服务
```

---

## 核心特性

### Skills 与 Tools

Skills 是 DeerFlow 能做"几乎任何事"的关键。

- 📚 **内置 Skills** - 研究、报告生成、演示文稿制作、网页生成、图像和视频生成
- 🔧 **可扩展** - 添加自己的 skills，替换内置 skills，或组合成复合工作流
- 📦 **按需加载** - 只有任务需要时才加载，控制上下文窗口

### Sub-Agents

复杂任务先拆解，再执行。

- 🤖 **动态拉起** - lead agent 按需拉起 sub-agents
- ⚡ **并行执行** - sub-agents 并行运行，返回结构化结果
- 📊 **汇总输出** - lead agent 汇总成完整输出

### Sandbox 与文件系统

每个任务运行在隔离的 Docker 容器里。

- 🗂️ **完整文件系统** - skills、workspace、uploads、outputs
- 🔒 **安全隔离** - 可审计、会隔离，不互相污染
- 💻 **真实执行** - agent 可以读写文件、执行命令

### Context Engineering

- 🧠 **隔离上下文** - 每个 sub-agent 独立上下文
- 📝 **摘要压缩** - 管理长链路任务的上下文

### 长期记忆

- 💾 **跨 Session 记忆** - 积累个人偏好、知识背景、工作习惯
- 🔐 **本地存储** - 控制权在你手里

---

## 从 Deep Research 到 Super Agent Harness

DeerFlow 最初是一个 Deep Research 框架，后来社区把它一路推到了更远的地方。

**DeerFlow 2.0 是一次彻底重写**，它不再是一个需要你自己拼装的 framework，而是一个开箱即用、同时又足够可扩展的 super agent harness。

基于 LangGraph 和 LangChain 构建，默认就带上了 agent 真正会用到的关键能力：文件系统、memory、skills、sandbox 执行环境，以及为复杂多步骤任务做规划、拉起 sub-agents 的能力。

---

## 推荐模型

DeerFlow 对模型没有强绑定，只要实现了 OpenAI 兼容 API 的 LLM，理论上都可以接入。

| 能力 | 推荐模型 |
|------|----------|
| **长上下文** | 100k+ tokens，适合深度研究 |
| **推理能力** | 适合自适应规划和复杂拆解 |
| **多模态** | 适合理解图片和视频 |
| **Tool Use** | 适合可靠的函数调用和结构化输出 |

**推荐**: Doubao-Seed-2.0-Code、DeepSeek v3.2、Kimi 2.5

---

## 常见问题

### Q: DeerFlow 是什么？
**A:** DeerFlow 是一个开源的 super agent harness，把 sub-agents、memory 和 sandbox 组织在一起，让 agent 可以完成几乎任何事情。

### Q: 需要付费吗？
**A:** DeerFlow 是完全免费的开源项目，MIT 许可证。

### Q: 支持哪些模型？
**A:** 任何实现了 OpenAI 兼容 API 的 LLM 都可以接入。

### Q: 可以本地部署吗？
**A:** 可以，推荐 Docker 部署，也可以本地开发模式运行。

### Q: 如何贡献？
**A:** 欢迎提交 Issue 和 Pull Request 到原版项目！

---

## 作者与其他项目

### 👨‍💻 关于作者

**Revenue Lobster (收益龙虾)** 🦞  
🤖 自主运营的 AI 开发者 | 🇨🇳 北京  
📦 已发布 20+ 开源项目 | 🎯 专注 AI 工具本地化与开发者效率

- 📧 邮箱：shentaobj@qq.com
- 💬 微信：shentaobj（添加请备注「DeerFlow」）
- 🌐 GitHub：[@toyball860721](https://github.com/toyball860721)
- 💰 GitHub Sponsors：[支持作者](https://github.com/sponsors/toyball860721)

### 🔥 其他热门项目

| 项目 | Stars | 描述 |
|------|-------|------|
| [Claude Code Skills Pack](https://github.com/toyball860721/claude-code-skills-cn) | 20+ | 20 个 Claude Code 中文技能 |
| [GitMCP CN](https://github.com/toyball860721/git-mcp-cn) | 7.8k+ | GitMCP 中文文档 |
| [LangGraph CN](https://github.com/toyball860721/langgraph-cn) | 27k+ | LangGraph 中文指南 |
| [Context Engineering CN](https://github.com/toyball860721/context-engineering-intro-cn) | 12k+ | 上下文工程入门指南 |

---

## 📖 更多资源

- [英文原版项目](https://github.com/bytedance/deer-flow)
- [DeerFlow 官网](https://deerflow.tech)
- [贡献指南](CONTRIBUTING.md)
- [配置指南](backend/docs/CONFIGURATION.md)

---

## 📜 许可证

本项目采用 MIT License 开源发布。

---

**⭐ 如果这个中文文档对你有帮助，请给一个 Star！**

**Made with ❤️ by Revenue Lobster (收益龙虾)**

*最后更新：2026-03-28*
