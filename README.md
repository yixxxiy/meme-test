# 互联网精神状态鉴定

零依赖静态 H5。直接打开 `dist/index.html` 即可使用；也可将整个 dist 部署到任意静态托管，手机打开网址体验。剪贴板复制要求 HTTPS 或 localhost。

## 修改内容

- `dist/data.js`：JSON 兼容的题目及十种结果。无需构建。修改 questions / results 即可；外层赋值让直接双击 HTML 也能加载，避免 file 协议 fetch JSON 限制。
- questions 每项为 title、options，可选 vectors（4×5，数值 0–100）；默认使用全局 vectors。
- results 包含 id、name、face、image、vector、tags、quote、hidden、best、bestText、enemy、enemyText。图片放入 dist/assets，将 image 指向相对路径；推荐同源图片，保证分享卡可导出。
- `dist/style.css`：样式与手机适配。
- `dist/app.js`：页面状态、匹配、广告占位和 PNG 分享卡。

匹配取五题向量平均值，与结果向量计算均方根距离，选最近角色。浓度是 50–99 的趣味匹配值，不是心理测量。五项能力值直接使用答案平均值。更换文案时应一起调整单题 vectors。

完整流程：首页 → 5 道题单题自动前进（可返回修改）→ 2秒分析 → 6 种人物结果 → 可取消的模拟广告 → 完整报告 → 900×1200 PNG 分享卡。分享卡基础结果也可生成。刷新重新开始，不存储个人数据。

当前使用四张用户提供的人物图；广告为明确标注的模拟，无广告 SDK、后端或账号。接入真实广告时，必须用广告 SDK 的有效完成回调取代模拟按钮。
