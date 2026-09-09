# concept-learning-kit

> 个人概念学习仓库：用一个自建的 **项目级 Skill** 生成、沉淀并迭代概念学习资料。
> 课程作业 1 交付物 · 作者：楼欣钰 · 最后更新：2026-09-09

---

## 1. 这个仓库是干什么的

我在学 AI 应用相关概念时有两个痛点：让 AI 解释一个概念，看完觉得懂了，过两天全忘；资料里全是 AI 的结论，没有自己的判断，讨论时说不出「我为什么这么理解」。

所以这个仓库做两件事：

1. **沉淀方法** —— 把「怎么学一个概念」固化成项目级 Skill `concept-study-guide`，换任何概念都能复用；
2. **沉淀产出** —— 把用这个 Skill 生成、并经人工核查修订的学习资料存下来，作为后续课程项目的个人工具基础和作品集材料。

它不是一次性作业目录，而是一个可以持续加东西的仓库：以后学新概念，就在 `learning-materials/` 里多一个文件；发现 Skill 有缺陷，就改 `SKILL.md` 再提交。

---

## 2. 目录结构

```
concept-learning-kit/
├── .workbuddy/
│   └── skills/
│       └── concept-study-guide/          # 项目级 Skill（核心）
│           ├── SKILL.md                  # 主文件：元数据 + 完整流程 + 自检清单
│           └── templates/
│               └── output-skeleton.md    # 输出骨架模板（按需加载）
├── learning-materials/                   # Skill 产出的学习资料
│   ├── agent.html                        # 概念一：Agent
│   ├── llm-context.html                  # 概念二：大模型的上下文
│   ├── skill.html                        # 概念三：Skill
│   └── concept-relationship.html         # 三者关系（可视化版）
├── docs/
│   └── concept-relationship.md           # 三者关系（文字版，含 Mermaid 图）
├── README.md
└── .gitignore                            # 排除密钥、隐私与临时文件
```

---

## 3. Skill 说明

**存放路径**：`.workbuddy/skills/concept-study-guide/SKILL.md`

放在仓库根目录下的 `.workbuddy/skills/` 里，属于**项目级 Skill**——它随仓库走，任何克隆这个仓库的人在 WorkBuddy / 同类工具中打开它都能直接使用，也可以提交到 Git 做版本管理。

**它能接收任意一个新概念**，不是为本次三个概念写的一次性提示词。SKILL.md 里定义了：

| 部分 | 内容 |
|---|---|
| 适用场景 | 什么情况该用、什么情况不该用 |
| 输入信息 | 6 个输入项（只有「概念」必填，其余有默认值） |
| 生成步骤 | 7 步流程，其中「检索并锁定来源」为不可跳过的强制步骤 |
| 输出结构 | 固定 12 节的骨架，缺一节视为不合格 |
| 格式要求 | 单文件 HTML、浅色主题、无外部依赖、可离线打开 |
| 资料来源要求 | ≥3 个来源、≥1 个一手来源、必须实际访问验证、禁止编造 URL |
| 自检要求 | 18 条清单，分内容准确性 / 结构完整性 / 可用性 / 可复用性四类 |
| 强制个人项 | 「我的理解」（本人改写）和「我的存疑点」（必须非空） |

设计上我最在意的两条硬规矩：**必须有个人解释**（不许照搬 AI 原文）、**来源必须可核查**（不许凭印象写链接）。

---

## 4. 如何在 WorkBuddy 中调用它

1. **克隆并打开仓库**
   ```bash
   git clone https://github.com/wwww673/concept-learning-kit.git
   ```
   在 WorkBuddy 中把该仓库目录作为工作区打开（项目级 Skill 只有在该仓库被打开时才生效）。

2. **直接说人话调用**（模型会根据 description 自动匹配）
   ```
   用 concept-study-guide 学一下「向量检索」
   ```

3. **带上更多输入项**（可选，不填则用默认值）
   ```
   用 concept-study-guide 学「KV Cache」：
   我的起点是知道 Transformer 但不懂推理优化，
   动机是准备面试，深度选深挖，输出 HTML。
   ```

4. **产出位置**：默认 `learning-materials/<概念英文名>.html`

5. **换概念时不需要改任何提示词**——这正是它作为 Skill（而非一次性 prompt）的意义。

---

## 5. 已生成的学习资料

| 文件 | 概念 | 内容要点 |
|---|---|---|
| `learning-materials/agent.html` | **Agent** | Workflow 与 Agent 的架构区分（控制权归属）、五部分组成、运行循环图、SWE-bench 用例、四类混淆辨析、4 条不该用的情况 |
| `learning-materials/llm-context.html` | **大模型的上下文** | 上下文的 7 类组成、注意力 n² 压力与 context rot、上下文工程 vs 提示词工程、四种管理手段、5 条使用边界 |
| `learning-materials/skill.html` | **Skill** | SKILL.md 结构与字段作用、三级渐进式披露、与 Prompt/MCP/CLAUDE.md/Subagent/微调的辨析、5 条不该用的情况 |
| `learning-materials/concept-relationship.html` | **三者关系**（可视化） | 闭环关系图（SVG）、上下文如何影响 Agent、Skill 如何沉淀知识、本次作业实例走查 |
| `docs/concept-relationship.md` | **三者关系**（文字版） | 同上，含 Mermaid 图与 4 条个人判断 |

每份资料统一包含：学习档案卡 · 学习目标 · 核心问题 · 核心机制（含图） · 最小心智模型 · **我的理解** · 具体应用场景 · 易混淆与使用边界 · 5 道自测题（含判分要点） · 可核查来源表 · **我的存疑点**。

---

## 6. AI 使用与人工核查记录

**分工说明（避免误解归属）**：本仓库的初稿由 AI 生成，我负责核查、改写与定稿。下面如实记录各自做了什么。

### 6.1 AI 已完成的核查（可复现）

| 核查项 | 方式 | 结果 |
|---|---|---|
| 全部外链可访问性 | 用 curl 逐个请求，记录 HTTP 状态码 | 10 个链接全部返回 200（见下表） |
| 来源是否为一手 | 逐条核对发布方 | 一手来源 8 个（Anthropic 官方 6 + arXiv 1 + MCP 官网 1），二手综述 1 个 |
| 输出结构完整性 | 按 SKILL.md 的 12 节骨架逐份比对 | 三份资料 12 节齐全，无空缺 |
| HTML 是否自包含 | 检查是否引用外部 CDN / 资源 | 无外部依赖，全部为内联 CSS 与手绘 SVG，可离线打开 |
| 敏感信息扫描 | 检查仓库内是否含密钥、密码、个人隐私 | 未发现；`.gitignore` 已排除 `.env`、`*.key`、`credentials.json` 等 |

已验证链接清单（2026-09-09）：

| 链接 | 状态码 |
|---|---|
| anthropic.com/engineering/building-effective-agents | 200 |
| anthropic.com/engineering/effective-context-engineering-for-ai-agents | 200 |
| anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | 200 |
| platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | 200 |
| code.claude.com/docs/en/skills | 200 |
| claude.com/blog/skills | 200 |
| academy.claude.com/courses/claude-platform-101/context-management | 200 |
| lilianweng.github.io/posts/2023-06-23-agent | 200 |
| arxiv.org/abs/2307.03172 | 200 |
| modelcontextprotocol.io | 200 |

### 6.2 我本人做的核查与修改

| # | 核查项 | 我的处理 |
|---|---|---|
| 1 | **来源内容与引用是否对得上** | 逐条打开来源页面，核对被引用的论断确实出自该文。其中把最初引用的「长上下文一定导致性能悬崖」改写为「性能梯度式下降」——原文明确说不是硬悬崖，初稿表述失真。 |
| 2 | **「我的理解」是否为 AI 原文** | 三份资料的「我的理解」全部由我本人重写，采用「类比 + 大白话 + 它其实不是什么」的固定句式，AI 初稿的对应段落已删除。 |
| 3 | **「我的存疑点」是否为空** | 按 Skill 要求，学完没疑问说明没学透。三份资料各补写了 2–3 条真实存疑点（如 context rot 缺少量化阈值、Skill 触发依赖语义匹配不可控）。 |
| 4 | **数字与硬事实** | 删除了初稿中几处无法溯源到具体来源的数字；token 量级（如元数据约 50–100 tokens、正文建议 <5k tokens）保留官方文档明确给出的数值。 |
| 5 | **个人化补充** | 在 Agent 与 Skill 两篇的「应用场景」中加入我自己的实例（本次作业中 Agent 帮建仓库、本次作业本身就是 Skill 的用例），而非只保留官方示例。 |
| 6 | **概念关系部分** | `docs/concept-relationship.md` 第 6 节「我的判断」4 条全部为我本人观点，其中第 2、4 条与资料来源的说法不完全一致，已明确标注为个人推测。 |
| 7 | **敏感信息与隐私** | 检查全部文件，确认不含 API Key、密码、学号外的个人敏感信息；`.gitignore` 补充了 `*.token`、`secret*/`、`.env.*` 等规则。 |

### 6.3 我明确没有照搬的部分

- 三份资料的「我的理解」「我的存疑点」章节：本人撰写。
- `docs/concept-relationship.md` 的「我的判断」章节：本人撰写。
- 所有来源链接：均实际访问确认，未使用 AI 凭印象生成的 URL。

---

## 7. 版本与安全

- **版本管理**：仓库使用 `main` 分支，按「Skill + 首批资料 → 关系说明 → README」分阶段提交，提交信息写明每步做了什么，便于回溯。
- **敏感信息处理**：
  - `.gitignore` 排除 `.env` / `.env.*`、`*.key`、`*.pem`、`credentials.json`、`service-account*.json`、`*.token`、`secret*/`、`private/` 等；
  - 全程未使用密码或写入任何令牌到仓库文件；推送使用 GitHub 个人访问令牌（PAT），仅存在于本地命令执行过程中，不落盘、不提交；
  - 学习资料中不引用任何需要登录才能访问的私有文档。
- **安全提醒**：Skill 可以包含可执行代码。本仓库的 Skill 仅含 Markdown 文件、不含脚本；若日后从外部引入第三方 Skill，按 Anthropic 官方建议应先通读其打包文件再启用。

---

## 8. 过程中遇到的问题与解决方式

| 问题 | 原因 | 解决方式 |
|---|---|---|
| `gh: command not found` | 本机未安装 GitHub CLI | 不依赖 `gh`，改用 Git 命令 + GitHub REST API 创建仓库 |
| `ssh: connect to host github.com port 22: Connection refused` | 网络环境封禁 22 端口 | 放弃 SSH 协议，改用 HTTPS（443）推送 |
| 无 GitHub 凭据 | 本机未配置令牌 | 由本人在 GitHub 生成只勾选 `repo` 权限的 PAT，通过 HTTPS 一次性完成推送，用后立即在 GitHub 端吊销 |

---

## 9. 后续计划

- 用同一个 Skill 继续生成新概念的学习资料（如 RAG、KV Cache、MCP），验证它换概念后无需修改即可复用；
- 根据使用中暴露的问题迭代 `SKILL.md`（已知待改进：自测题难度分级、来源可信度评分）；
- 后续课程项目继续在本仓库基础上添加新的个人 Skill。

---

## 10. 许可

内容仅用于个人学习与课程作业。资料中的观点与来源链接归原作者所有，引用处均已标注。
