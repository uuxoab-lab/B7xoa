# CLAUDE.md

本文件告诉 Claude Code 如何在这个仓库里工作。仓库是 **Des-CTF-Knowledge** 的中文 CTF 知识库快照。

## 仓库是什么

- 12 类 Web 漏洞深度文章（SQL 注入、RCE、文件上传、文件包含、SSRF、SSTI、JWT、PHP 反序列化、PHP 代码审计、命令执行、图片隐写、音频隐写、压缩包）
- 1156 篇历年大赛 WP 的结构化 meta（`.meta.md`，11 字段）
- 386 场大赛索引
- 50+ 解题脚本
- `PAYLOAD-CHEATSHEET.md` 十大类高频 Payload 速查

## 工作方式（重要）

**不要一次性读整个仓库，也不要整篇读大文件。** 按下面的顺序：

1. **先读 `AI-SEARCH-INDEX.md`**（约 200 行）。它是全局检索索引，先用它定位到具体文件。
2. 大文章旁有配套的 `.idx.md` 分段索引，例如 `PHP反序列化漏洞总结.idx.md`。先读 idx 拿到行号，再用 `Read` 的 `offset` / `limit` 精确读那一段。
3. 需要原文细节时再读正文，避免把 6000+ 行的文件整个塞进上下文。

## 目录结构

```
AI-SEARCH-INDEX.md        # 全局索引，优先读
PAYLOAD-CHEATSHEET.md     # Payload 速查，做题先翻这里
SQL.md / 命令执行.md / 文件上传漏洞.md / 文件包含.md / SSRF漏洞.md
PHP反序列化漏洞总结.md / php代码审计.md / SSTI.md / JWT.md
图片隐写.md / 音频隐写.md / 压缩包总结.md
CTF大赛WP集合/articles/    # 1156 篇 .meta.md
WP汇总/                    # ctfshow / SQLI-LABS 等靶场 WP
CTF常用脚本及工具/          # 50+ 脚本，含 SCRIPTS-INDEX.md
工具使用/                   # sqlmap / ffuf / Dirsearch / Wireshark / tshark / 内存取证
```

## 常用检索

```bash
grep -rn "关键词" --include="*.md" .
grep -A 20 "SQL注入" PAYLOAD-CHEATSHEET.md
ls CTF大赛WP集合/articles/ | grep -i "反序列化"
cat CTF常用脚本及工具/SCRIPTS-INDEX.md
```

## WP meta 的 11 个字段

`title` / `contest` / `year` / `difficulty` / `vuln_type` / `tags` / `attack_chain` / `key_payload` / `one_liner` / `lesson` / `quality`

找题时按 `vuln_type`、`tags`、`year`、`contest` 过滤。

## 回答要求

- 引用内容时给出**文件路径和行号**，方便回查。
- 涉及利用链时，优先给可以直接复制的 payload 或命令，再讲原理。
- 不确定就说不确定，不要编造仓库里没有的 WP 或脚本。
- 本仓库内容是安全研究与教学用途，回答时保持这个定位。
