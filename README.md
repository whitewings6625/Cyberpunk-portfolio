# Cyberpunk-portfolio
# 我將先建立一個簡易的 HTML/CSS/JS 架構，依照使用者所提供的設計規格
# 完整內容會包含首頁、動畫標題、三個主題模組與子分類預覽結構

from pathlib import Path

# 建立檔案結構
base_path = Path("/mnt/data/cyberpunk_site")
base_path.mkdir(parents=True, exist_ok=True)

# index.html
index_html = """<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>關於◼︎◼︎◼︎◼︎的可能性演算</title>
  <link href="style.css" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&display=swap" rel="stylesheet">
</head>
<body>
  <div class="container">
    <h1 class="main-title">【 關於 <span class="glitch" data-real="異形">◼︎◼︎◼︎◼︎</span> 的可能性演算 】</h1>
    
    <div class="module-list">
      <div class="module" onclick="openModule('base')">▍既定結構基礎演算法</div>
      <div class="module" onclick="openModule('alien')">▍關於異形的可能性演算</div>
      <div class="module" onclick="openModule('elden')">▍關於法環的可能性演算</div>
    </div>

    <div id="panel" class="panel hidden">
      <div id="subtitles" class="subtitles">
        <div class="subtitle">▍關於這個宇宙／世界／可能性</div>
        <div class="subtitle">▍關於伊利亞</div>
        <div class="subtitle">▍關於哈里斯</div>
      </div>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>
"""

# style.css
style_css = """
body {
  margin: 0;
  padding: 0;
  font-family: 'Share Tech Mono', monospace;
  background-color: black;
  color: white;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  height: 100vh;
  padding-top: 50px;
}

.container {
  text-align: center;
}

.main-title {
  font-size: 24px;
  margin-bottom: 40px;
}

.glitch {
  display: inline-block;
  color: white;
  position: relative;
  cursor: pointer;
}

.glitch:hover::before {
  content: attr(data-real);
  position: absolute;
  left: 2px;
  top: 0;
  color: cyan;
  text-shadow: -1px 0 red;
  animation: glitchAnim 0.3s;
}

.module-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
}

.module {
  padding: 12px 20px;
  border: 1px solid cyan;
  background: transparent;
  cursor: pointer;
  transition: 0.3s;
}

.module:hover {
  background: rgba(0, 255, 255, 0.1);
  box-shadow: 0 0 10px cyan;
}

.panel {
  margin-top: 40px;
  padding: 20px;
  border: 1px solid cyan;
  background: rgba(255, 255, 255, 0.05);
}

.hidden {
  display: none;
}

.subtitles {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
"""

# script.js
script_js = """
function openModule(type) {
  document.getElementById('panel').classList.remove('hidden');
}
"""

# 儲存檔案
(base_path / "index.html").write_text(index_html, encoding="utf-8")
(base_path / "style.css").write_text(style_css, encoding="utf-8")
(base_path / "script.js").write_text(script_js, encoding="utf-8")

# 回傳檔案下載路徑
base_path