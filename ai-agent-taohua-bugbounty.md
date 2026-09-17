# AI-Driven Bug Bounty Skill — How `taohua-bugbounty` Works

> 类型：AI 工作流 / Claude Code skill 方法论
> 声明：公开整体设计与思路；私有实现细节不外泄。

## Why I built it
(我为什么要用 AI agent 做挖洞：重复步骤自动化、提高覆盖面、把精力留给需要判断的地方)

## The Pipeline (recon → enumerate → test → report)
一个打通流程的蓝图：
1. **Recon / Asset Discovery** — 用哪些工具（amass、subfinder 等）做子域/资产枚举，结果如何归集
2. **Enumerate** — 端口/目录/技术栈识别（nmap、ffuf、katana），如何去重、怎么判断面
3. **Test** — 把发现整理成待测清单，人工判断 + AI 辅助分析（代码/配置/请求差异）
4. **Report** — 结果落成可复现 writeup（链接到本仓库的 writeup-pentest 风格）

## How the skill is structured (design)
- **Skill 逻辑**：把流程拆成模块（`recon`、`enum`、`test`、`report`），每个模块做什么、输入输出是什么
- **提示词 / 约束**：为什么限制 AI 只做"建议 + 依据"，不盲改参数（可控性）
- **工具链组合**：哪些 CLI 工具被 skill 编排（amass/subfinder/ffuf/nuclei/katana），怎么避免误伤（scope 控制）

## Where AI adds real value
- 大规模任务的**并行与覆盖面**
- 代码/配置审查的**初步发现**
- 报告与 writeup 的**结构化输出**

## Where AI does NOT replace humans
- 业务逻辑判断、WAF/绕过的临场变通、授权边界判断——仍靠人

## Result / Evidence
- 用这套 skill 在授权 SRC / Bugcrowd 上产生的效果（**可核验**：链接到 Bugcrowd profile，不写敏感金额）

## Lessons
- 一句话总结：自动化服务判断，判断服务结果。