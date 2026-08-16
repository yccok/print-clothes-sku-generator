# print-clothes-sku-generator（印花服饰编码生成器）— DSH Skill

一个给 **DeepSeek Harness（DSH）** Agent 使用的 Skill：让模型掌握"印花服饰 SKU 编码生成器"（Excel VBA / BigSeller）的源码结构、编码规则与扩展方法，能够直接读码、改码、查 bug，并按模板扩展新国家仓库。

## 功能

- **源码随包**：两份正式单仓源码（越南男装 / 泰国男装）放在 `assets/`，模型可随时读取分析
- **编码规范**：单件 / 组合 SKU 格式、纯色代号（越南 `T`/`M`、泰国 `TT`/`TM`）、缩写规则
- **差异分析**：8 个参数化差异点 + "模板法"扩展新国家仓库（童装版同构规律）
- **已知坑位**：VBA Dictionary 崩溃、业务代号与代码硬编码差异、清空范围不足等

## 安装

1. **环境要求**：DeepSeek Harness 0.1.0-rc.6 或兼容的后续 0.1.x 版本
2. **下载**：Clone 或下载本仓库 zip，解压后把整个 `print-clothes-sku-generator` 文件夹放到任意技能根目录：
   - 用户全局（任何项目可用）：`~/.dsh/skills/`（Windows：`C:\Users\<用户名>\.dsh\skills\`）
   - 项目级（仅该项目生效）：`<项目根>/.dsh/skills/`
3. **注意**：GitHub zip 解压后文件夹名会带 `-main` 后缀（如 `print-clothes-sku-generator-main`），**必须改回 `print-clothes-sku-generator`**（目录名需与 SKILL.md 里的 `name` 一致，否则不会被识别）
4. **验证**：重启 DSH（或新开会话），技能目录出现 `print-clothes-sku-generator` 即成功

## 使用

会话中直接提及"编码生成器""生成器""SKU 生成""BigSeller"等关键词，Agent 会自动加载本 skill；也可用 skill 工具手动加载 `print-clothes-sku-generator`。加载后模型可读取 `assets/` 内的源码并按手册工作（校验、生成编码、导出单品/组合装表、按差异点扩展新仓库）。

## 目录结构

```
print-clothes-sku-generator/
├─ SKILL.md                        ← 操作手册（DSH 技能入口，含 frontmatter）
├─ assets/
│  ├─ 越南男装编码生成器源码.txt     ← 越南仓男装版（纯色代号 M）
│  └─ 泰国男装编码生成器源码.txt     ← 泰国仓男装版（纯色代号 TM）
├─ README.md
└─ LICENSE
```

## 关于 assets 中的源码

两份源码是业务生成器的正式版本，随 skill 打包以保证"读码/改码"能力自包含。**公开本仓库即公开这两份源码**——如需保密，请使用私有仓库或自行移除 `assets/`（移除后 skill 仍可加载，但模型将无法直接读取源码）。

## 许可

MIT License，详见 [LICENSE](LICENSE)。
