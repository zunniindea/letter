<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>민아 누나에게 보내는 작은 상자</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css">
<link href="https://fonts.googleapis.com/css2?family=Gowun+Dodum&family=Gaegu:wght@400;700&display=swap" rel="stylesheet">

<style>
:root {
  --bg-paper:#FAF7F2;
  --bg-card:#FFF;
  --bg-warm:#F3EDE2;
  --bg-note:#FFF9DB;
  --ink-main:#2C2825;
  --ink-sub:#6E675F;
  --ink-muted:#A39B90;
  --accent-coral:#E07A5F;
  --accent-coral-soft:#F9E5DF;
  --accent-sage:#7A9E7E;
  --border-line:#E6DFD3;
  --shadow-soft:0 10px 30px -5px rgba(44,40,37,.07),0 4px 12px -2px rgba(44,40,37,.04);
  --shadow-card:0 4px 16px rgba(44,40,37,.06);
  --ease-out-expo:cubic-bezier(.22,1,.36,1);
  --ease-spring:cubic-bezier(.34,1.56,.64,1);
}
* {box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body {
  width:100%;min-height:100dvh;background:#EFECE6;color:var(--ink-main);
  font-family:'Pretendard',-apple-system,BlinkMacSystemFont,sans-serif;
  line-height:1.6;overflow-x:hidden;
}
.app-shell {
  position:relative;width:100%;max-width:440px;min-height:100dvh;margin:0 auto;
  background-color:var(--bg-paper);
  background-image:radial-gradient(#D8D0C5 .75px,transparent .75px);
  background-size:20px 20px;box-shadow:0 0 40px rgba(0,0,0,.06);
  display:flex;flex-direction:column;overflow:hidden;
}
.handwriting {font-family:'Gaegu','Gowun Dodum',cursive,sans-serif}
.serif-soft {font-family:'Gowun Dodum',sans-serif}
.top-bar {
  position:sticky;top:0;z-index:30;display:flex;align-items:center;
  justify-content:space-between;padding:14px 20px;
  background:rgba(250,247,242,.88);backdrop-filter:blur(8px);
  border-bottom:1px dashed var(--border-line);
}
.top-bar.hidden-bar {opacity:0;pointer-events:none}
.step-dots {display:flex;gap:8px;align-items:center}
.step-dot {
  width:8px;height:8px;border-radius:999px;background:var(--border-line);
  border:0;padding:0;cursor:pointer;transition:all .35s var(--ease-out-expo);
}
.step-dot.active {width:24px;background:var(--accent-coral)}
.top-title {font-size:13px;color:var(--ink-sub);font-weight:500;letter-spacing:-.02em}
.screen-container {flex:1;position:relative;display:flex;flex-direction:column}
.screen {
  display:none;flex-direction:column;flex:1;padding:28px 22px 44px;
  opacity:0;transform:translateY(14px);
  transition:opacity .5s var(--ease-out-expo),transform .5s var(--ease-out-expo);
}
.screen.active-screen {display:flex;opacity:1;transform:translateY(0)}
.intro-wrap {
  flex:1;display:flex;flex-direction:column;align-items:center;
  justify-content:center;text-align:center;padding:20px 10px;
}
.to-badge {
  display:inline-flex;align-items:center;gap:6px;padding:6px 14px;
  background:var(--bg-warm);border:1px solid var(--border-line);
  border-radius:999px;font-size:13px;color:var(--ink-sub);margin-bottom:18px;
}
.intro-title {font-size:24px;font-weight:700;letter-spacing:-.03em;margin-bottom:8px}
.intro-sub {font-size:15px;color:var(--ink-sub);margin-bottom:36px;min-height:24px}
.gift-stage {
  position:relative;width:200px;height:200px;display:flex;align-items:center;
  justify-content:center;cursor:pointer;user-select:none;margin-bottom:28px;
}
.gift-box-btn {position:relative;width:150px;height:140px;background:none;border:0;cursor:pointer;padding:0}
.box-shadow {
  position:absolute;bottom:6px;left:50%;transform:translateX(-50%);
  width:130px;height:18px;background:rgba(44,40,37,.08);border-radius:50%;
  transition:all .5s var(--ease-out-expo);
}
.box-body {
  position:absolute;bottom:14px;left:15px;width:120px;height:92px;
  background:#F4EAE1;border:2.5px solid var(--ink-main);
  border-radius:6px 6px 10px 10px;overflow:hidden;z-index:2;
}
.box-body::before,.box-lid::before {
  content:'';position:absolute;left:50%;top:0;transform:translateX(-50%);
  width:22px;height:100%;background:var(--accent-coral);
  border-left:2px solid var(--ink-main);border-right:2px solid var(--ink-main);
}
.box-inner-card {
  position:absolute;bottom:30px;left:50%;
  transform:translateX(-50%) translateY(20px) rotate(-4deg);
  width:92px;height:70px;background:#FFFDF9;border:2px solid var(--ink-main);
  border-radius:6px;z-index:1;display:flex;flex-direction:column;
  align-items:center;justify-content:center;opacity:0;
  transition:all .55s var(--ease-spring);box-shadow:0 4px 10px rgba(0,0,0,.08);
}
.box-lid {
  position:absolute;top:22px;left:7px;width:136px;height:30px;
  background:#F9F1E8;border:2.5px solid var(--ink-main);border-radius:6px;
  z-index:4;transform-origin:center bottom;transition:all .55s var(--ease-spring);
}
.box-ribbon {
  position:absolute;top:-2px;left:50%;transform:translateX(-50%);
  width:56px;height:28px;z-index:5;transition:all .55s var(--ease-spring);
}
.box-ribbon::before,.box-ribbon::after {
  content:'';position:absolute;bottom:0;width:24px;height:20px;
  border:2.5px solid var(--ink-main);background:var(--accent-coral);
  border-radius:50% 50% 0 50%;transform:rotate(-18deg);left:2px;
}
.box-ribbon::after {border-radius:50% 50% 50% 0;transform:rotate(18deg);left:auto;right:2px}
.gift-box-btn.shake {animation:boxWobble .45s ease}
@keyframes boxWobble {
  0%,100%{transform:rotate(0) scale(1)}
  20%{transform:rotate(-7deg) scale(1.04)}
  45%{transform:rotate(7deg) scale(1.05)}
  70%{transform:rotate(-4deg) scale(1.02)}
}
.gift-box-btn.opened .box-lid {transform:translateY(-48px) rotate(16deg);opacity:0}
.gift-box-btn.opened .box-ribbon {transform:translateX(-50%) translateY(-56px) rotate(22deg);opacity:0}
.gift-box-btn.opened .box-inner-card {
  opacity:1;transform:translateX(-50%) translateY(-44px) rotate(2deg) scale(1.08);z-index:5;
}
.gift-box-btn.opened .box-shadow {width:145px;opacity:.5}
.tap-hint {
  display:inline-flex;align-items:center;gap:6px;font-size:13px;color:var(--ink-muted);
  background:#FFF;padding:8px 16px;border-radius:999px;border:1px dashed var(--border-line);
}
.section-header {margin-bottom:22px}
.section-tag {
  display:inline-block;font-size:12px;font-weight:600;color:var(--accent-coral);
  background:var(--accent-coral-soft);padding:4px 10px;border-radius:6px;margin-bottom:8px;
}
.section-title {font-size:21px;font-weight:700;letter-spacing:-.03em;margin-bottom:4px}
.section-desc {font-size:14px;color:var(--ink-sub)}
.drawing-grid {
  display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:16px;margin-bottom:22px;
}
.drawing-grid.single-item {grid-template-columns:1fr;max-width:320px;margin-left:auto;margin-right:auto}
.polaroid-card {
  position:relative;background:#FFF;border:1.5px solid var(--border-line);
  border-radius:14px;padding:12px 12px 14px;box-shadow:var(--shadow-card);
  cursor:pointer;transition:transform .3s var(--ease-out-expo),box-shadow .3s var(--ease-out-expo);
  display:flex;flex-direction:column;text-align:left;min-width:0;
}
.polaroid-card:nth-child(odd){transform:rotate(-1deg)}
.polaroid-card:nth-child(even){transform:rotate(1.2deg)}
.polaroid-card:hover,.polaroid-card:active {transform:rotate(0) translateY(-3px);box-shadow:var(--shadow-soft)}
.masking-tape {
  position:absolute;top:-8px;left:50%;transform:translateX(-50%) rotate(-2deg);
  width:58px;height:16px;background:rgba(235,216,188,.72);
  border-left:1px dashed rgba(163,155,144,.4);border-right:1px dashed rgba(163,155,144,.4);
  pointer-events:none;z-index:2;
}
.drawing-frame {
  width:100%;aspect-ratio:1;background:#FCFBF9;border:1px solid #EFEAE1;
  border-radius:9px;overflow:hidden;display:flex;align-items:center;
  justify-content:center;margin-bottom:10px;position:relative;
}
.drawing-frame img {width:100%;height:100%;object-fit:contain;display:block;padding:6px}
.drawing-placeholder {
  width:100%;height:100%;display:flex;flex-direction:column;align-items:center;
  justify-content:center;gap:8px;color:#B8B0A5;font-size:12px;
}
.drawing-placeholder .plus {font-size:28px;font-weight:300}
.drawing-caption-title {
  font-size:14px;font-weight:600;margin-bottom:2px;display:flex;
  align-items:flex-start;justify-content:space-between;gap:4px;
}
.drawing-caption-title>span:first-child {overflow-wrap:anywhere}
.drawing-caption-sub {font-size:12.5px;color:var(--ink-sub);line-height:1.45;word-break:keep-all}
.like-pill {
  flex-shrink:0;font-size:11px;color:var(--accent-coral);background:var(--accent-coral-soft);
  padding:2px 7px;border-radius:999px;font-weight:600;
}
.upload-helper-box {
  background:var(--bg-warm);border:1px dashed #CFC6B8;border-radius:12px;
  padding:12px 14px;margin-bottom:24px;display:flex;align-items:center;
  justify-content:space-between;gap:10px;
}
.upload-helper-text {font-size:12.5px;color:var(--ink-sub);line-height:1.4}
.upload-btn-label {
  flex-shrink:0;background:#FFF;border:1px solid var(--border-line);color:var(--ink-main);
  font-size:12px;font-weight:600;padding:7px 12px;border-radius:8px;cursor:pointer;
}
.memo-grid {display:flex;flex-direction:column;gap:12px;margin-bottom:24px}
.memo-card {
  background:#FFF;border:1.5px solid var(--border-line);border-radius:14px;
  padding:15px 16px;text-align:left;cursor:pointer;transition:all .3s var(--ease-out-expo);
  position:relative;box-shadow:0 2px 8px rgba(44,40,37,.03);width:100%;font:inherit;
}
.memo-card.revealed {background:var(--bg-note);border-color:#E8D89A}
.memo-top {display:flex;align-items:center;justify-content:space-between;gap:8px;margin-bottom:4px}
.memo-badge {font-size:12px;font-weight:700;color:var(--ink-sub)}
.memo-status {font-size:11.5px;color:var(--ink-muted);white-space:nowrap}
.memo-front-text {font-size:15px;font-weight:600;color:var(--ink-main)}
.memo-secret-text {
  display:none;margin-top:8px;padding-top:8px;border-top:1px dashed #E2D39C;
  font-size:14px;color:#4A4238;line-height:1.55;
}
.memo-card.revealed .memo-secret-text {display:block;animation:fadeSlideDown .3s var(--ease-out-expo)}
@keyframes fadeSlideDown {
  from{opacity:0;transform:translateY(-4px)}
  to{opacity:1;transform:translateY(0)}
}
.easter-egg-zone {
  margin:6px 0 24px;padding:14px;border-radius:12px;
  background:rgba(243,237,226,.6);border:1px dashed var(--border-line);
  display:flex;align-items:center;justify-content:space-between;gap:12px;
}
.sleeping-cat-btn {
  background:#FFF;border:1.5px solid var(--border-line);border-radius:10px;
  padding:8px 12px;font-size:13px;color:var(--ink-main);cursor:pointer;
  display:inline-flex;align-items:center;gap:6px;white-space:nowrap;
}
.cat-speech {font-size:13px;color:var(--ink-sub);flex:1;text-align:right}
.envelope-stage {display:flex;flex-direction:column;align-items:center;margin:12px 0 24px;width:100%}
.envelope-wrapper {
  position:relative;width:100%;max-width:330px;height:210px;background:#EFE3D2;
  border:2px solid var(--ink-main);border-radius:10px;box-shadow:var(--shadow-soft);
  cursor:pointer;display:flex;align-items:center;justify-content:center;
  transition:all .5s var(--ease-out-expo);overflow:hidden;
}
.envelope-flap {
  position:absolute;top:0;left:0;width:100%;height:110px;background:#E5D5BE;
  clip-path:polygon(0 0,100% 0,50% 100%);transform-origin:top center;
  transition:transform .55s var(--ease-out-expo);z-index:3;
}
.envelope-seal {
  position:relative;z-index:4;background:var(--accent-coral);color:#FFF;
  border:2px solid var(--ink-main);padding:7px 16px;border-radius:999px;
  font-size:13px;font-weight:700;box-shadow:0 3px 8px rgba(0,0,0,.12);
}
.envelope-wrapper.opened-env {height:76px;margin-bottom:-14px;background:#E8D9C5;cursor:default}
.envelope-wrapper.opened-env .envelope-flap {transform:rotateX(180deg);opacity:.3}
.envelope-wrapper.opened-env .envelope-seal {opacity:0;pointer-events:none}
.letter-sheet {
  display:none;width:100%;background:#FFFDF9;border:1.5px solid #DED6C8;
  border-radius:14px;padding:26px 22px 28px;box-shadow:var(--shadow-soft);
  position:relative;z-index:5;
  background-image:repeating-linear-gradient(transparent,transparent 31px,#F1ECE1 31px,#F1ECE1 32px);
  line-height:32px;
}
.letter-sheet.show-letter {display:block;animation:unfoldPaper .6s var(--ease-out-expo)}
@keyframes unfoldPaper {
  from{opacity:0;transform:translateY(-20px) scaleY(.85)}
  to{opacity:1;transform:translateY(0) scaleY(1)}
}
.letter-date {font-size:12.5px;color:var(--ink-muted);text-align:right;line-height:1.4;margin-bottom:12px}
.letter-body {font-size:15.5px;color:var(--ink-main);white-space:pre-line;word-break:keep-all;line-height:32px}
.letter-sign {margin-top:18px;text-align:right;font-weight:700;font-size:15px;line-height:1.4}
.outro-card {
  background:#FFF;border:1.5px solid var(--border-line);border-radius:18px;
  padding:28px 22px;text-align:center;box-shadow:var(--shadow-card);margin:auto 0;
}
.outro-doodle {
  width:88px;height:88px;margin:0 auto 16px;background:var(--bg-warm);
  border-radius:50%;display:flex;align-items:center;justify-content:center;border:1.5px dashed #D5CBBF;
}
.outro-title {font-size:20px;font-weight:700;margin-bottom:8px}
.outro-desc {font-size:14.5px;color:var(--ink-sub);margin-bottom:22px;word-break:keep-all}
.happy-check-box {background:var(--bg-paper);border:1px solid var(--border-line);border-radius:12px;padding:16px;margin-bottom:20px}
.happy-question {font-size:14px;font-weight:600;margin-bottom:10px}
.happy-btn-group {display:flex;gap:8px;justify-content:center}
.happy-choice-btn {
  flex:1;padding:10px 8px;border-radius:9px;border:1.5px solid var(--ink-main);
  background:#FFF;font-size:13.5px;font-weight:600;color:var(--ink-main);cursor:pointer;
}
.happy-choice-btn.selected-choice {background:var(--accent-coral);color:#FFF;border-color:var(--ink-main)}
.happy-reply-msg {margin-top:12px;font-size:13.5px;font-weight:600;color:var(--accent-coral);min-height:20px}
.nav-btn-row {margin-top:auto;padding-top:16px;display:flex;gap:10px}
.primary-btn {
  flex:1;padding:14px 12px;border-radius:12px;border:2px solid var(--ink-main);
  background:var(--ink-main);color:#FFF;font-size:15px;font-weight:600;cursor:pointer;
}
.primary-btn:active {transform:scale(.98)}
.secondary-btn {
  padding:14px 16px;border-radius:12px;border:1.5px solid var(--border-line);
  background:#FFF;color:var(--ink-sub);font-size:14px;font-weight:600;cursor:pointer;
}
.modal-backdrop {
  position:fixed;inset:0;z-index:100;background:rgba(30,27,24,.72);
  backdrop-filter:blur(4px);display:none;align-items:center;justify-content:center;padding:20px;
}
.modal-backdrop.open-modal {display:flex;animation:fadeIn .25s ease}
@keyframes fadeIn {from{opacity:0}to{opacity:1}}
.modal-card {
  width:100%;max-width:360px;background:#FFFDF9;border:2px solid var(--ink-main);
  border-radius:18px;padding:18px 18px 20px;box-shadow:0 20px 50px rgba(0,0,0,.25);
}
.modal-img-box {
  width:100%;aspect-ratio:1;background:#FCFBF9;border:1px solid var(--border-line);
  border-radius:12px;display:flex;align-items:center;justify-content:center;overflow:hidden;margin-bottom:14px;
}
.modal-img-box img {width:100%;height:100%;object-fit:contain;padding:8px}
.modal-title {font-size:17px;font-weight:700;margin-bottom:4px}
.modal-desc {font-size:14px;color:var(--ink-sub);margin-bottom:16px;line-height:1.5}
.modal-actions {display:flex;gap:8px}
.heart-toggle-btn,.modal-close-btn {padding:11px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer}
.heart-toggle-btn {flex:1;border:1.5px solid var(--border-line);background:#FFF;color:var(--ink-main)}
.heart-toggle-btn.liked {background:var(--accent-coral-soft);border-color:var(--accent-coral);color:var(--accent-coral)}
.modal-close-btn {padding:11px 18px;border:1.5px solid var(--ink-main);background:var(--ink-main);color:#FFF}
.tap-spark {
  position:fixed;pointer-events:none;z-index:90;font-size:15px;color:var(--accent-coral);
  animation:floatUpFade .85s var(--ease-out-expo) forwards;
}
@keyframes floatUpFade {
  0%{opacity:.95;transform:translate(-50%,-50%) scale(.7)}
  100%{opacity:0;transform:translate(-50%,-140%) scale(1.15) rotate(12deg)}
}
@media(max-width:360px) {
  .screen{padding-left:16px;padding-right:16px}
  .drawing-grid{gap:10px}
  .polaroid-card{padding:9px}
  .drawing-caption-title{font-size:12px}
  .like-pill{font-size:10px;padding:2px 5px}
}
@media(prefers-reduced-motion:reduce) {
  *,*::before,*::after{animation-duration:.01ms!important;transition-duration:.01ms!important;scroll-behavior:auto!important}
}
</style>
</head>

<body>
<div class="app-shell" id="appShell">

  <header class="top-bar hidden-bar" id="topBar">
    <span class="top-title" id="topStepLabel">1 / 4 · 그림 모음</span>
    <div class="step-dots">
      <button class="step-dot" id="dot1" data-step="1" aria-label="그림 공간"></button>
      <button class="step-dot" id="dot2" data-step="2" aria-label="쿠폰함"></button>
      <button class="step-dot" id="dot3" data-step="3" aria-label="편지함"></button>
      <button class="step-dot" id="dot4" data-step="4" aria-label="마무리"></button>
    </div>
  </header>

  <main class="screen-container">

    <!-- 첫 화면: 선물 상자 -->
    <section class="screen active-screen" id="screen0">
      <div class="intro-wrap">
        <div class="to-badge">
          <span>📌</span><span id="introBadgeText">To. 민아 누나</span>
        </div>
        <h1 class="intro-title" id="introMainTitle">누나 이거 한번 눌러봐</h1>
        <p class="intro-sub" id="introSubText">누나 주려고 조금씩 시간 내서 만들어봤어</p>

        <div class="gift-stage">
          <button class="gift-box-btn" id="giftBoxBtn" aria-label="선물 상자 열기">
            <div class="box-ribbon"></div>
            <div class="box-lid"></div>
            <div class="box-inner-card">
              <span style="font-size:20px">🐾</span>
              <span class="handwriting" style="font-size:13px;font-weight:700;margin-top:2px">도착!</span>
            </div>
            <div class="box-body"></div>
            <div class="box-shadow"></div>
          </button>
        </div>
        <div class="tap-hint" id="boxTapHint">상자 눌러서 열어봐</div>
      </div>
    </section>

    <!-- 그림 갤러리: 기본 그림 없이 비워 둠 -->
    <section class="screen" id="screen1">
      <div class="section-header">
        <span class="section-tag">누나 전용 그림장</span>
        <h2 class="section-title" id="galleryTitle">틈날 때마다 그린 거</h2>
        <p class="section-desc" id="galleryDesc">누나가 내가 그린 거 다 저장해 뒀길래 몇 개 모아봤어. 누르면 크게 보여!</p>
      </div>

      <div class="drawing-grid" id="drawingGrid"></div>

      <div class="upload-helper-box">
        <div class="upload-helper-text">
          <strong>✏️ 내 그림 바로 넣어보기</strong><br>
          갤러리에서 내가 그린 사진을 고르면 화면에 바로 들어가!
        </div>
        <label class="upload-btn-label" for="localDrawingInput">사진 고르기</label>
        <input type="file" id="localDrawingInput" accept="image/*" multiple hidden>
      </div>

      <div class="nav-btn-row">
        <button class="primary-btn" id="toScreen2Btn">다음 거 보기 →</button>
      </div>
    </section>

    <!-- 쿠폰함 -->
    <section class="screen" id="screen2">
      <div class="section-header">
        <span class="section-tag">하나씩 눌러봐</span>
        <h2 class="section-title">누나한테 주는 작은 쿠폰함</h2>
        <p class="section-desc">카드를 누르면 숨겨진 메모가 나와</p>
      </div>

      <div class="memo-grid" id="memoGrid"></div>

      <div class="easter-egg-zone">
        <button class="sleeping-cat-btn" id="sleepingCatBtn">
          <span id="catEmoji">💤</span>
          <span id="catBtnLabel">자는 고양이 깨우기</span>
        </button>
        <span class="cat-speech" id="catSpeechText">쿨쿨 자는 중... (건드려 봐)</span>
      </div>

      <div class="nav-btn-row">
        <button class="secondary-btn" id="backTo1Btn">← 이전</button>
        <button class="primary-btn" id="toScreen3Btn">편지 봉투 열러 가기 →</button>
      </div>
    </section>

    <!-- 편지 -->
    <section class="screen" id="screen3">
      <div class="section-header">
        <span class="section-tag">짧은 쪽지</span>
        <h2 class="section-title">봉투도 한번 열어봐</h2>
        <p class="section-desc" id="envelopeHintText">가운데 빨간 스티커를 누르면 편지가 펼쳐져</p>
      </div>

      <div class="envelope-stage">
        <div class="envelope-wrapper" id="envelopeBox" role="button" tabindex="0" aria-label="편지 봉투 열기">
          <div class="envelope-flap"></div>
          <div class="envelope-seal" id="envelopeSealBtn">눌러서 열기 ✉️</div>
        </div>

        <article class="letter-sheet serif-soft" id="letterSheet">
          <div class="letter-date" id="letterDateText"></div>
          <div class="letter-body" id="letterBodyText"></div>
          <div class="letter-sign" id="letterSignText"></div>
        </article>
      </div>

      <div class="nav-btn-row">
        <button class="secondary-btn" id="backTo2Btn">← 이전</button>
        <button class="primary-btn" id="toScreen4Btn">마지막 화면으로 →</button>
      </div>
    </section>

    <!-- 마지막 화면 -->
    <section class="screen" id="screen4">
      <div class="outro-card">
        <div class="outro-doodle">
          <svg width="52" height="52" viewBox="0 0 80 80" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M22 36 L26 18 L36 28 L44 28 L54 18 L58 36 C62 46 58 58 40 58 C22 58 18 46 22 36 Z" fill="#FFFDF9" stroke="#2C2825" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
            <circle cx="32" cy="40" r="2.5" fill="#2C2825"/>
            <circle cx="48" cy="40" r="2.5" fill="#2C2825"/>
            <path d="M36 45 Q40 48 44 45" stroke="#2C2825" stroke-width="2.5" stroke-linecap="round"/>
            <circle cx="27" cy="44" r="3.5" fill="#F4A28C" opacity=".65"/>
            <circle cx="53" cy="44" r="3.5" fill="#F4A28C" opacity=".65"/>
          </svg>
        </div>

        <h2 class="outro-title" id="outroTitleText">구경 다 했어?</h2>
        <p class="outro-desc" id="outroDescText">앞으로도 내가 그림 그릴 때마다 여기 하나씩 더 채워 넣을게.</p>

        <div class="happy-check-box">
          <div class="happy-question">선물 마음에 들어? 행복해?</div>
          <div class="happy-btn-group">
            <button class="happy-choice-btn" id="choiceHappy1">ㅇㄱㄹㅇ 엉!</button>
            <button class="happy-choice-btn" id="choiceHappy2">완전 마음에 들어</button>
          </div>
          <div class="happy-reply-msg" id="happyReplyMsg"></div>
        </div>

        <div class="nav-btn-row" style="padding-top:4px">
          <button class="secondary-btn" id="backTo3Btn">← 편지 다시 보기</button>
          <button class="primary-btn" id="restartAllBtn">처음부터 다시 보기 ↺</button>
        </div>
      </div>
    </section>
  </main>
</div>

<!-- 그림 확대 모달 -->
<div class="modal-backdrop" id="drawingModal">
  <div class="modal-card">
    <div class="modal-img-box" id="modalImgContainer"></div>
    <h3 class="modal-title" id="modalTitle"></h3>
    <p class="modal-desc" id="modalDesc"></p>
    <div class="modal-actions">
      <button class="heart-toggle-btn" id="modalHeartBtn">🤍 하트 꾹</button>
      <button class="modal-close-btn" id="modalCloseBtn">닫기</button>
    </div>
  </div>
</div>

<script>
/* =========================================================
   직접 수정하는 설정 구역
   ========================================================= */

// 첫 화면 문구
const INTRO_CONFIG = {
  toName: "To. 민아 누나",
  mainTitle: "누나 이거 한번 눌러봐",
  subTitle: "심심해서 누나 주려고 직접 좀 만들어봤어",
  firstTapMessage: "오 흔들린다.. 한 번만 더 눌러봐!"
};

/*
  그림 넣는 방법:
  1. GitHub 저장소에 images 폴더를 만든다.
  2. 직접 그린 그림 파일을 그 폴더에 업로드한다.
  3. 아래 imageFile에 경로를 적는다.
  예: imageFile: "images/mydrawing.jpg"

  imageFile을 빈 문자열로 두면 그림이 없는 빈 공간으로 표시된다.
*/
const DRAWINGS_LIST = [
  {
    id: "draw-1",
    imageFile: "21527.jpg",
    title: "물고기를 생각하는 냥이",
    description: "파란 물고기 꿈을 꾸는 고양이",
    liked: false
  },
  {
    id: "draw-2",
    imageFile: "21529.png",
    title: "바보냥이",
    description: "바보같아 누나같네",
    liked: false
  },
  {
    id: "draw-3",
    imageFile: "21531.png",
    title: "잘햇어요 냥이",
    description: "칭찬할때마다 써줄게",
    liked: false
  },
  {
    id: "draw-4",
    imageFile: "",
    title: "",
    description: "곧 추가야",
    liked: false
  }
];

// 쿠폰 02, 03을 제거했으며 01, 04만 유지
const SECRET_MEMOS = [
  {
    badge: "쿠폰 01 · 모닝콜",
    frontTitle: "⏰ 예준이의 모닝콜 이용권",
    secretMessage: "주말에 시간 되면 누나가 원할때 내가 모닝콜 해줄게"
  },
  {
    badge: "쿠폰 04 · 맛집 탐방",
    frontTitle: "🍳 요리 꿈나무 픽 맛집 투어",
    secretMessage: "누나가 고른 맛있는 곳 어디든 같이 가기. 만나면 내가 맛있는 거 꼭 산다!"
  }
];

// 편지 내용
const LETTER_CONFIG = {
  date: "2026년 가을, 누나 생각하면서",
  body: `안녕 누나. 최근에 디엠으로는 긴 글 많이 보냈으니까, 이번엔 조금 다르게 내가 직접 작은 공간을 하나 만들어봤어.

맨날 그림만 그려서 보내다가, 누나가 내가 그린 거 하나도 안 빼놓고 갤러리에 다 저장해 둔 거 보고 아예 누나만 꺼내 볼 수 있는 그림장을 만들어주고 싶었거든.

솔직히 이거 만들면서도 누나가 보면 또 귀엽다면서 바보라고 웃겠지 싶었는데, 그래도 누나가 구경하면서 한 번이라도 피식 웃으면 난 그걸로 진짜 뿌듯할 것 같아.

요즘 매일 통화하면서 누나 목소리 듣고, 같이 한참 동안 웃고 떠드는 시간이 내 하루 중에 제일 재밌어. 서로 불렀던 노래도 그렇고, 누나랑 얘기할 때가 제일 편하고 좋다.

우리 조만간 만나면 맛있는 것도 먹으러 가고 재밌게 놀자. 앞으로도 학교에서 그림 그릴 때마다 여기 하나씩 더 채워 넣을게!`,
  sign: "- 예준이가"
};

/* =========================================================
   아래는 사이트 동작 코드
   ========================================================= */

let currentStep = 0;
let boxTapCount = 0;
let catTapCount = 0;
let activeModalIndex = null;

// 빈 그림 공간. 그림을 넣기 전에는 이 화면이 표시된다.
function getEmptyDrawing() {
  return `
    <div class="drawing-placeholder">
      <span class="plus">＋</span>
      <span>여기에 그림 넣기</span>
    </div>
  `;
}

// 화면 전환
function goToStep(stepNumber) {
  currentStep = stepNumber;

  document.querySelectorAll(".screen").forEach((screen, index) => {
    screen.classList.toggle("active-screen", index === stepNumber);
  });

  const topBar = document.getElementById("topBar");
  const topLabel = document.getElementById("topStepLabel");
  const titles = [
    "",
    "1 / 4 · 그림 모음",
    "2 / 4 · 쿠폰함",
    "3 / 4 · 편지함",
    "4 / 4 · 마무리"
  ];

  if (stepNumber === 0) {
    topBar.classList.add("hidden-bar");
  } else {
    topBar.classList.remove("hidden-bar");
    topLabel.textContent = titles[stepNumber] || "";
  }

  for (let i = 1; i <= 4; i++) {
    const dot = document.getElementById("dot" + i);
    if (dot) dot.classList.toggle("active", i === stepNumber);
  }

  window.scrollTo({ top: 0, behavior: "smooth" });
}

// 그림 갤러리
function renderDrawings() {
  const grid = document.getElementById("drawingGrid");
  grid.innerHTML = "";
  grid.classList.toggle("single-item", DRAWINGS_LIST.length === 1);

  DRAWINGS_LIST.forEach((item, index) => {
    const card = document.createElement("button");
    card.type = "button";
    card.className = "polaroid-card";
    card.setAttribute("aria-label", item.title);

    const frame = document.createElement("div");
    frame.className = "drawing-frame";

    if (item.imageFile && item.imageFile.trim() !== "") {
      const img = document.createElement("img");
      img.src = item.imageFile;
      img.alt = item.title;
      img.onerror = () => {
        frame.innerHTML = getEmptyDrawing();
      };
      frame.appendChild(img);
    } else {
      frame.innerHTML = getEmptyDrawing();
    }

    const tape = document.createElement("div");
    tape.className = "masking-tape";

    const titleRow = document.createElement("div");
    titleRow.className = "drawing-caption-title";

    const title = document.createElement("span");
    title.textContent = item.title;

    const like = document.createElement("span");
    like.className = "like-pill";
    like.textContent = item.liked ? "❤️ 저장됨" : "🤍 내 그림";

    titleRow.append(title, like);

    const description = document.createElement("p");
    description.className = "drawing-caption-sub";
    description.textContent = item.description;

    card.append(tape, frame, titleRow, description);
    card.addEventListener("click", () => openDrawingModal(index));
    grid.appendChild(card);
  });
}

// 그림 확대 모달
function openDrawingModal(index) {
  activeModalIndex = index;
  const item = DRAWINGS_LIST[index];
  const modal = document.getElementById("drawingModal");
  const container = document.getElementById("modalImgContainer");

  container.innerHTML = "";

  if (item.imageFile && item.imageFile.trim() !== "") {
    const img = document.createElement("img");
    img.src = item.imageFile;
    img.alt = item.title;
    img.onerror = () => container.innerHTML = getEmptyDrawing();
    container.appendChild(img);
  } else {
    container.innerHTML = getEmptyDrawing();
  }

  document.getElementById("modalTitle").textContent = item.title;
  document.getElementById("modalDesc").textContent = item.description;
  updateModalHeartButton(item.liked);
  modal.classList.add("open-modal");
}

function updateModalHeartButton(isLiked) {
  const button = document.getElementById("modalHeartBtn");
  button.classList.toggle("liked", isLiked);
  button.textContent = isLiked ? "❤️ 저장됨" : "🤍 하트 꾹";
}

// 쿠폰 렌더링
function renderMemos() {
  const grid = document.getElementById("memoGrid");
  grid.innerHTML = "";

  SECRET_MEMOS.forEach((memo) => {
    const card = document.createElement("button");
    card.type = "button";
    card.className = "memo-card";

    const top = document.createElement("div");
    top.className = "memo-top";

    const badge = document.createElement("span");
    badge.className = "memo-badge";
    badge.textContent = memo.badge;

    const status = document.createElement("span");
    status.className = "memo-status";
    status.textContent = "눌러서 열어보기 ▾";

    top.append(badge, status);

    const title = document.createElement("div");
    title.className = "memo-front-text";
    title.textContent = memo.frontTitle;

    const secret = document.createElement("div");
    secret.className = "memo-secret-text";
    secret.textContent = memo.secretMessage;

    card.append(top, title, secret);

    card.addEventListener("click", () => {
      const revealed = card.classList.toggle("revealed");
      status.textContent = revealed ? "열림 ✨" : "눌러서 열어보기 ▾";
    });

    grid.appendChild(card);
  });
}

function initApp() {
  // 첫 화면 문구
  document.getElementById("introBadgeText").textContent = INTRO_CONFIG.toName;
  document.getElementById("introMainTitle").textContent = INTRO_CONFIG.mainTitle;
  document.getElementById("introSubText").textContent = INTRO_CONFIG.subTitle;

  // 편지
  document.getElementById("letterDateText").textContent = LETTER_CONFIG.date;
  document.getElementById("letterBodyText").textContent = LETTER_CONFIG.body;
  document.getElementById("letterSignText").textContent = LETTER_CONFIG.sign;

  renderDrawings();
  renderMemos();

  const giftBoxBtn = document.getElementById("giftBoxBtn");
  const introSubText = document.getElementById("introSubText");
  const boxTapHint = document.getElementById("boxTapHint");

  // 선물 상자 열기
  giftBoxBtn.addEventListener("click", () => {
    boxTapCount++;

    if (boxTapCount === 1) {
      giftBoxBtn.classList.remove("shake");
      void giftBoxBtn.offsetWidth;
      giftBoxBtn.classList.add("shake");
      introSubText.textContent = INTRO_CONFIG.firstTapMessage;
      boxTapHint.textContent = "한 번 더 누르면 열려!";
    } else {
      giftBoxBtn.classList.add("opened");
      introSubText.textContent = "열렸다! 잠깐만 기다려봐";
      boxTapHint.textContent = "선물 꺼내는 중...";
      setTimeout(() => goToStep(1), 850);
    }
  });

  // 휴대폰에서 그림 파일을 선택해 미리보기
  document.getElementById("localDrawingInput").addEventListener("change", (event) => {
    const files = Array.from(event.target.files || []);
    if (!files.length) return;

    files.forEach((file) => {
      if (!file.type.startsWith("image/")) return;

      const reader = new FileReader();

      reader.onload = (e) => {
        const dataUrl = e.target.result;
        const emptyIndex = DRAWINGS_LIST.findIndex(item => !item.imageFile);

        if (emptyIndex !== -1) {
          DRAWINGS_LIST[emptyIndex].imageFile = dataUrl;
          DRAWINGS_LIST[emptyIndex].title =
            file.name.replace(/\.[^/.]+$/, "");
        } else {
          DRAWINGS_LIST.push({
            id: "draw-custom-" + Date.now() + "-" + Math.random().toString(36).slice(2),
            imageFile: dataUrl,
            title: file.name.replace(/\.[^/.]+$/, ""),
            description: "내가 직접 그린 그림!",
            liked: false
          });
        }

        renderDrawings();
      };

      reader.readAsDataURL(file);
    });

    // 같은 사진을 다시 선택해도 change 이벤트가 발생하도록 초기화
    event.target.value = "";
  });

  // 자는 고양이 이스터에그
  const catBtn = document.getElementById("sleepingCatBtn");
  const catEmoji = document.getElementById("catEmoji");
  const catSpeech = document.getElementById("catSpeechText");

  catBtn.addEventListener("click", () => {
    catTapCount++;

    if (catTapCount === 1) {
      catEmoji.textContent = "🐱";
      catSpeech.textContent = "음냐.. 생선 꿈꾸는 중인데 왜 깨워..";
    } else if (catTapCount === 2) {
      catEmoji.textContent = "🐟";
      catSpeech.textContent = "생선 내놔라 바보야!";
    } else {
      catEmoji.textContent = "😻";
      catSpeech.textContent = "누나 오늘도 기분 좋은 하루 보내!";
      catTapCount = 0;
    }
  });

  // 편지 봉투 열기
  const envelopeBox = document.getElementById("envelopeBox");
  const letterSheet = document.getElementById("letterSheet");
  const envelopeHintText = document.getElementById("envelopeHintText");

  function openEnvelope() {
    if (!envelopeBox.classList.contains("opened-env")) {
      envelopeBox.classList.add("opened-env");
      letterSheet.classList.add("show-letter");
      envelopeHintText.textContent = "편지가 펼쳐졌어! 천천히 읽어봐";
    }
  }

  envelopeBox.addEventListener("click", openEnvelope);
  envelopeBox.addEventListener("keydown", (event) => {
    if (event.key === "Enter" || event.key === " ") {
      event.preventDefault();
      openEnvelope();
    }
  });

  // 상단 점 네비게이션
  document.querySelectorAll(".step-dot").forEach((dot) => {
    dot.addEventListener("click", () => {
      const targetStep = Number(dot.dataset.step);
      if (targetStep) goToStep(targetStep);
    });
  });

  // 화면 이동 버튼
  document.getElementById("toScreen2Btn").addEventListener("click", () => goToStep(2));
  document.getElementById("backTo1Btn").addEventListener("click", () => goToStep(1));
  document.getElementById("toScreen3Btn").addEventListener("click", () => goToStep(3));
  document.getElementById("backTo2Btn").addEventListener("click", () => goToStep(2));
  document.getElementById("toScreen4Btn").addEventListener("click", () => goToStep(4));
  document.getElementById("backTo3Btn").addEventListener("click", () => goToStep(3));

  // 마지막 화면의 선택 버튼
  const choice1 = document.getElementById("choiceHappy1");
  const choice2 = document.getElementById("choiceHappy2");
  const replyMsg = document.getElementById("happyReplyMsg");

  choice1.addEventListener("click", () => {
    choice1.classList.add("selected-choice");
    choice2.classList.remove("selected-choice");
    replyMsg.textContent = "누나가 행복하면 나두 행복하지!";
  });

  choice2.addEventListener("click", () => {
    choice2.classList.add("selected-choice");
    choice1.classList.remove("selected-choice");
    replyMsg.textContent = "다행이다! 만들면서 뿌듯했어";
  });

  // 처음부터 다시 보기
  document.getElementById("restartAllBtn").addEventListener("click", () => {
    boxTapCount = 0;
    giftBoxBtn.classList.remove("opened", "shake");
    introSubText.textContent = INTRO_CONFIG.subTitle;
    boxTapHint.textContent = "상자를 톡톡 눌러서 열어봐";

    envelopeBox.classList.remove("opened-env");
    letterSheet.classList.remove("show-letter");
    envelopeHintText.textContent = "가운데 빨간 스티커를 누르면 편지가 펼쳐져";

    document.querySelectorAll(".memo-card").forEach(card => {
      card.classList.remove("revealed");
      const status = card.querySelector(".memo-status");
      if (status) status.textContent = "눌러서 열어보기 ▾";
    });

    choice1.classList.remove("selected-choice");
    choice2.classList.remove("selected-choice");
    replyMsg.textContent = "";

    goToStep(0);
  });

  // 그림 모달 닫기
  const modal = document.getElementById("drawingModal");

  document.getElementById("modalCloseBtn").addEventListener("click", () => {
    modal.classList.remove("open-modal");
  });

  modal.addEventListener("click", (event) => {
    if (event.target === modal) modal.classList.remove("open-modal");
  });

  document.addEventListener("keydown", (event) => {
    if (event.key === "Escape") modal.classList.remove("open-modal");
  });

  // 그림 하트 토글
  document.getElementById("modalHeartBtn").addEventListener("click", () => {
    if (activeModalIndex === null) return;

    DRAWINGS_LIST[activeModalIndex].liked =
      !DRAWINGS_LIST[activeModalIndex].liked;

    updateModalHeartButton(DRAWINGS_LIST[activeModalIndex].liked);
    renderDrawings();
  });

  // 배경 터치 장식
  document.getElementById("appShell").addEventListener("click", (event) => {
    if (
      event.target.closest("button") ||
      event.target.closest("label") ||
      event.target.closest("#envelopeBox") ||
      event.target.closest("input")
    ) return;

    const symbols = ["✦", "🐾", "🍀", "🐟"];
    const spark = document.createElement("span");
    spark.className = "tap-spark";
    spark.textContent = symbols[Math.floor(Math.random() * symbols.length)];
    spark.style.left = event.clientX + "px";
    spark.style.top = event.clientY + "px";

    document.body.appendChild(spark);
    setTimeout(() => spark.remove(), 850);
  });
}

window.addEventListener("DOMContentLoaded", initApp);
</script>
</body>
</html>
