# zGames

单机网页游戏合集。每款游戏是一个自带全部内容的 `.htm` 文件，发布在
`https://zzn.im/g/<game-name>`（带不带 `.htm` 都能打开）。

## 目录结构

```
zGames/
├── g/
│   ├── index.html     # 游戏列表页 → zzn.im/g/
│   ├── strike.htm     # 第一人称射击 → zzn.im/g/strike
│   └── conquest.htm   # 策略游戏   → zzn.im/g/conquest
├── vercel.json        # 静态部署 + 去掉 .htm 的 rewrite
└── AGENTS.md          # 给 AI 代理的约定
```

## 发布链路

```
浏览器 → zzn.im/g/strike
          │  (zzn-im-2026 仓库的 vercel.json 把 /g/* 转发过来)
          ▼
        zgames Vercel 项目 → /g/strike → rewrite → g/strike.htm
```

推送到 `main` 后 Vercel 自动部署。PR 会得到预览地址。

## 加一款新游戏

1. 新建 `g/<game-name>.htm`。名字只用小写字母、数字和连字符。
2. 在 `g/index.html` 的列表里加一项。
3. 本地预览：`npx serve .` 后打开 `http://localhost:3000/g/<game-name>.htm`。

## 约定

- 单文件：HTML、CSS、JS 和素材（程序生成或 data URI）都写在同一个 `.htm` 里。
  第三方库只从 CDN 加载并锁定版本号，例如 `three@0.160.0`。
- 单机：不需要后端，不收集数据。存档用 `localStorage`。
- 原创：玩法可以借鉴类型，但不用任何现有游戏的名称、角色、地图、美术和音乐。
- 桌面和手机都要能玩，或者在手机上明确提示需要键盘鼠标。
