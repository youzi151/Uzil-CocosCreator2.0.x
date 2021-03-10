# Uzil-CocosCreator2.0

## 簡介

自用工具集，對應CocosCreator版本2.0.10

以簡易、方便開發使用為主，不想做得太偏介面化或框架化。

盡量功能分拆，減少"工具去干涉遊戲主循環"或者"主循環必須依循框架而寫"的狀況。

各功能的目錄結構也分開，避免工具與專案項目的檔案混淆。

## 更新紀錄

目前 v0.1.0 (2021-03-09)

詳見 [ChangeLog](CHANGELOG.md)


## 核心功能

為其他功能所使用之功能。本身較無明顯的單獨應用。

- Invoker 呼叫器
  - 簡化、方便的計時呼叫。
  - 基於Update生命週期管理。
- Event 事件
  - 提供 事件偵聽與呼叫。
  - 偵聽者 可設置 呼叫排序、限制次數。
  - 提供 EventBus系統。
- Time 時間控制
  - 提供 多個 設置user 設 不同的timeScale與優先度。
  - 以不同實體取得timeScale, deltaTime...等資訊。
- Bezier, Curve 曲線
- Values 數值管理
  - 提供 多個 設置user 設 不同的值與優先度
  - 提供 取用user 取得 單一個值 (最優先者)
- Async 異步執行 (參考async.js)

## 基礎功能

比較與引擎有關聯的功能。

- Animator 動畫狀態機
  - 支援 Spine, 內建Anim。
  - 提供 動畫狀態管理, 統一呼叫介面。
- Shuriken 仿粒子系統
  - 設置並發射 Prefab。
- Shader 渲染
  - 簡易實現 材質與渲染
- i18n 多語系
  - 在場景中以Node與各個i18nComponent進行設置
  - 讀取urlArgs中的lang或執行時更換語言

## 進階功能

為方便項目開發，所逐一添加的功能。

- AudioMgr 音效管理
  - 註冊名稱與實際資源之連結後，方便以名稱管理音效。
  - 提供 Layer分層管理音量。
- PageCard 頁卡控制
  - 管理並切換不同頁面的各卡片(物件)開關。
  - 以字串進行頁面設定與呼叫。
- State 狀態控制
  - 管理並切換各狀態。
  - 提供切換時的行為介面。
- AniTween 簡單動態 (久未維護)
  - 拖放建立簡易動態 (e.g. 旋轉, 擺動...等)。

## 使用說明

### 功能區分

每一個功能為單位，其中含有自己使用的資源或lib(若無須與其他共用)。

分類狀況如：
- Uzil (總集合)
  - Advance (進階層分類)
    - PageCard (功能)
    - State (功能)
    - ... (功能)
  - Basic (基礎層分類)
    - ... (功能)
  - Core (核心層分類)
    - ... (功能)
  - UI (UI元件分類)
    - ... (功能)
  - Util (公用功能)
  - Macro (零碎功能)

### 依賴關係
大致上為：核心<-基礎<-進階，同階層的功能有盡量各自獨立。可以將不需要的功能移除後使用，只是要記得檢查該功能有無依賴更上層的功能。

### 代碼引用
以 [Uzil.ts](assets/import_out/Uzil/Uzil.ts) 統一作為對外或各功能相互的引用管道，避免資料夾結構更動後，有引用某A功能的某B代碼中，引用路徑遭大幅度破壞。
``` typescript
// 引用方式 舉例：
import { Invoker, Event, ClassName1, ClassName2 } from "../../Uzil";
```

### 代碼風格

- 大括號不換行
- tab縮排
- ...其餘自行參考

## 授權使用

詳見 [License](LICENSE)

## 參考/使用 其他項目

- Shader
  - Creator2.0 Shader (ericchen888)
    - 來源: https://forum.cocos.org/t/creator-2-0-shader/64755
  - 以及 其他cocos論壇上提供之代碼
- bezierjs (Pomax)
  - 來源: https://pomax.github.io/bezierjs/