# tinymindcony · 项目状态

> 2026-09-26 仓库整理时生成。事实来源：README（上游 TinyMind 的）、`git log`、所有者记忆笔记。

## 项目
- TinyMind（mazzzystar 的开源博客/备忘，数据存 GitHub 仓库）的个人 fork，已迁到 Cloudflare Workers（opennextjs-cloudflare），去掉 tinymind.me 自定义域、vars 全指 workers.dev、sitemap 用户改 tuziani。
- 平台：Next.js → Cloudflare Worker `tinymind`。
- 线上：https://tinymind.conylab.workers.dev ——**目前是坏的**（首页 404 / sitemap 1042，旧配置遗留），本地已修好等部署。
- 仓库 `tuziani/tinymindcony`（HTTPS）；本地 `~/Documents/Code/tinymindcony`。

## 当前状态
- main `f8538df`（09-20，停止跟踪 `.claude/settings.local.json`）干净、与 origin 一致；上一次实质改动是 08-08 去品牌化（`eb0ca2a`）。
- **部署阻塞**：`wrangler.jsonc` 要求 secrets `GITHUB_ID` / `GITHUB_SECRET`（NextAuth GitHub OAuth），Worker 上只有 `GITHUB_TOKEN` / `NEXTAUTH_SECRET`。GitHub OAuth App 无法用 API 建。

## 进行中 / WIP 分支
- 无 wip/ 或 archive/ 分支。

## 下一步
1. 所有者手动在 https://github.com/settings/applications/new 建 OAuth App（callback `https://tinymind.conylab.workers.dev/api/auth/callback/github`）。
2. 拿到 ID/secret 后 `npx wrangler secret put GITHUB_ID` / `GITHUB_SECRET` → `npm run deploy`。
3. 部署后核对首页 / sitemap / 登录。

## 已知坑
- README 仍是上游原文（tinymind.me、Chrome 扩展等与本 fork 无关），未改写。
- 历史 306 个提交里绝大多数是上游作者的；只有 3 个是本 fork 的。
