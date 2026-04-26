# db-man-v7

手機版台股看盤與技術分析工具。專案以單頁靜態網頁實作，使用者可在瀏覽器中載入本機 `.db` 股票資料，不需要後端伺服器。

## 主要功能

- 排行榜：漲幅榜、跌幅榜、漲停板、成交量、成交額、量增長、量比、連續上漲、突破、週線與月線排行。
- 技術分析：K 線圖、成交量圖、均線、量均線、十字線資訊同步、漲跌顏色邏輯。
- 股票資訊卡：股票名稱、代號、價格、三角形漲跌、開高低收量即時跟隨十字線更新。
- 自選股：加入、移除、追蹤與檢視自選清單。
- 統計頁：漲跌停統計、個股成交量熱力圖、類股表現排行。
- 手機版排版：針對手機寬度設計，包含底部導覽、浮動按鈕、可收合篩選列。
- 主題切換：支援白天與黑夜模式。
- PWA：包含 manifest 與 service worker，可作為網頁 App 使用。

## 使用方式

1. 開啟 `index.html`。
2. 點右上角「載入」。
3. 選取一個或多個 `.db` 股票資料檔。
4. 載入完成後即可查看排行、技術分析、自選股與統計資料。

## 資料格式

本工具使用 `sql.js` 在瀏覽器端讀取 SQLite `.db` 檔案。資料表與欄位需符合專案目前的解析邏輯，至少需要包含股票代號、名稱、日期、開高低收、成交量等日線資料。

目前分時、1 分、5 分資料尚未實作，因此技術分析頁中的分時按鈕為停用狀態。

## 技術架構

- HTML / CSS / JavaScript
- sql.js：瀏覽器端 SQLite 讀取
- Lightweight Charts：K 線與成交量圖表
- ECharts：統計圖與熱力圖
- Bootstrap Icons / Font Awesome：圖示
- PWA manifest / service worker

## 專案檔案

- `index.html`：主要程式與 UI
- `manifest.json`：PWA 設定
- `sw.js`：service worker
- `icon.svg`、`icon-192.png`、`icon-512.png`：App 圖示

## 部署

本專案是靜態網站，可直接部署到 GitHub Pages、Netlify、Cloudflare Pages 或任何靜態檔案伺服器。

若使用 GitHub Pages，請確認：

- repository 已啟用 Pages
- source 指向 `main` 分支
- 根目錄包含 `index.html`

## 注意事項

- 股票資料由使用者自行提供，本專案不內建即時行情資料。
- 所有 `.db` 檔案都在瀏覽器端讀取，不會上傳到伺服器。
- 若瀏覽器封鎖本機檔案功能，建議使用簡單靜態伺服器或 GitHub Pages 開啟。
