<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<title>Atlas</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,700&family=Source+Sans+3:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap');

:root{
  --bg: #EDE6D6;
  --bg-dot: rgba(32,40,60,0.05);
  --surface: #F7F2E7;
  --surface-2: #FBF8F0;
  --text: #2B2620;
  --text-muted: rgba(43,38,32,0.6);
  --line: rgba(32,40,60,0.18);
  --rust: #B5482E;
  --sage: #6B7560;
  --gold: #BF9A2A;
  --sidebar-bg: #20283C;
  --sidebar-text: #F7F2E7;
  --sidebar-text-dim: rgba(233,228,214,0.7);
  --sidebar-active: rgba(233,228,214,0.1);
  --font-display: 'Fraunces', serif;
  --font-body: 'Source Sans 3', sans-serif;
}

body[data-theme="nacht"]{
  --bg: #161A26;
  --bg-dot: rgba(237,230,214,0.04);
  --surface: #1F2536;
  --surface-2: #242B40;
  --text: #EDE6D6;
  --text-muted: rgba(237,230,214,0.6);
  --line: rgba(237,230,214,0.16);
  --rust: #D4684A;
  --sage: #8B9A85;
  --gold: #D8B23F;
  --sidebar-bg: #0E111A;
  --sidebar-text: #EDE6D6;
  --sidebar-text-dim: rgba(237,230,214,0.65);
  --sidebar-active: rgba(237,230,214,0.08);
}

body[data-theme="kontrast"]{
  --bg: #FFFFFF;
  --bg-dot: rgba(0,0,0,0.06);
  --surface: #FFFFFF;
  --surface-2: #FFFFFF;
  --text: #000000;
  --text-muted: #333333;
  --line: #000000;
  --rust: #B5482E;
  --sage: #3C4A37;
  --gold: #8A6A00;
  --sidebar-bg: #000000;
  --sidebar-text: #FFFFFF;
  --sidebar-text-dim: rgba(255,255,255,0.7);
  --sidebar-active: rgba(255,255,255,0.14);
}

body[data-font="mono"]{ --font-display: 'JetBrains Mono', monospace; --font-body: 'JetBrains Mono', monospace; }
body[data-font="klassisch"]{ --font-display: Georgia, 'Times New Roman', serif; --font-body: Helvetica, Arial, sans-serif; }

*{box-sizing:border-box;}
html,body{margin:0;padding:0;}
body{
  background:
    radial-gradient(circle at 1px 1px, var(--bg-dot) 1px, transparent 0),
    var(--bg);
  background-size: 14px 14px;
  color: var(--text);
  font-family: var(--font-body);
  min-height: 100vh;
  transition: background .2s ease, color .2s ease;
}

h1,h2,h3,.display{ font-family: var(--font-display); font-weight: 600; letter-spacing: -0.01em; }
.mono{ font-family:'JetBrains Mono', monospace; }

/* ---------- LANGUAGE SWITCH (global) ---------- */
#lang-switch{
  position: fixed; top: 16px; right: 16px; z-index: 80;
  display:flex; gap:2px; background: var(--surface); border:1px solid var(--line);
  border-radius: 4px; padding:3px; box-shadow: 0 6px 16px -8px rgba(0,0,0,0.3);
}
#lang-switch button{
  border:none; background:transparent; cursor:pointer; padding:6px 9px; border-radius:3px;
  font-family:'JetBrains Mono', monospace; font-size:11px; font-weight:600; letter-spacing:0.04em;
  color: var(--text-muted);
}
#lang-switch button.active{ background: var(--sidebar-bg); color: var(--sidebar-text); }

/* ---------- AUTH SCREEN ---------- */
#screen-auth{ min-height:100vh; display:flex; align-items:center; justify-content:center; padding: 24px; }

.passport{
  width: 100%; max-width: 420px; background: var(--surface); border: 1px solid var(--line);
  border-radius: 4px; box-shadow: 0 1px 0 rgba(32,40,60,0.06), 0 18px 40px -20px rgba(32,40,60,0.35);
  position: relative; overflow: hidden;
}
.passport::before{
  content:""; position:absolute; top:0; left:0; right:0; height:6px;
  background: repeating-linear-gradient(90deg, var(--rust) 0 12px, transparent 12px 18px); opacity:0.7;
}
.passport-inner{ padding: 40px 36px 32px; }
.eyebrow{ font-family:'JetBrains Mono', monospace; font-size: 11px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--rust); margin-bottom: 6px; }
.passport h1{ font-size: 30px; margin: 0 0 4px; }
.passport .sub{ color: var(--text-muted); font-size: 14px; margin-bottom: 28px; }

.field{ margin-bottom: 16px; }
.field label{ display:block; font-size: 12px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--text-muted); margin-bottom: 6px; }
.field input{
  width:100%; padding: 11px 12px; border: 1px solid var(--line); border-bottom: 2px solid var(--sidebar-bg);
  border-radius: 2px; background: var(--surface-2); font-family: var(--font-body); font-size: 15px; color: var(--text);
}
.field input:focus{ outline: 2px solid var(--gold); outline-offset: 1px; }

.btn{ appearance:none; border: none; cursor: pointer; font-family: var(--font-body); font-weight: 600; font-size: 15px; border-radius: 3px; padding: 12px 18px; transition: transform .12s ease; }
.btn:active{ transform: translateY(1px); }
.btn-primary{ background: var(--sidebar-bg); color: var(--sidebar-text); width:100%; }
.btn-primary:hover{ filter: brightness(1.12); }
.btn-ghost{ background: transparent; color: var(--text); border: 1px solid var(--line); }
.btn-ghost:hover{ background: rgba(127,127,127,0.08); }
.btn-small{ padding: 7px 12px; font-size:13px; }
.btn-danger-text{ background:none; border:none; color:var(--rust); cursor:pointer; font-size:13px; text-decoration:underline; padding:0; }

.auth-toggle{ display:flex; gap:6px; margin-bottom: 26px; background: rgba(127,127,127,0.1); padding:4px; border-radius:4px; }
.auth-toggle button{ flex:1; padding:8px; border:none; background:transparent; cursor:pointer; font-family:var(--font-body); font-size:13px; font-weight:600; color: var(--text-muted); border-radius:3px; }
.auth-toggle button.active{ background: var(--surface); color: var(--text); box-shadow: 0 1px 2px rgba(0,0,0,0.1); }

.auth-msg{ font-size: 13px; margin-top: 14px; min-height: 18px; }
.auth-msg.error{ color: var(--rust); }
.auth-msg.ok{ color: var(--sage); }

.stamp{
  position:absolute; bottom: 22px; right: 26px; width: 64px; height: 64px;
  border: 2px solid rgba(181,72,46,0.35); border-radius: 50%;
  display:flex; align-items:center; justify-content:center; transform: rotate(-12deg);
  font-family:'JetBrains Mono'; font-size: 9px; letter-spacing: 0.05em; color: rgba(181,72,46,0.5);
  text-align:center; line-height:1.3; pointer-events:none;
}

/* ---------- APP SHELL ---------- */
#screen-app{ display:none; min-height:100vh; }
.shell{ display:grid; grid-template-columns: 240px 1fr; min-height: 100vh; }
.sidebar{ background: var(--sidebar-bg); color: var(--sidebar-text); padding: 28px 18px; display:flex; flex-direction: column; }
.brand{ font-family: var(--font-display); font-size:21px; font-weight:700; color: var(--sidebar-text); margin-bottom:2px; }
.brand-sub{ font-family:'JetBrains Mono'; font-size:10px; letter-spacing:0.12em; color: var(--sidebar-text-dim); text-transform:uppercase; margin-bottom: 34px; }

.nav-item{ display:flex; align-items:center; gap:10px; padding: 11px 12px; border-radius: 3px; cursor:pointer; font-size: 14px; color: var(--sidebar-text-dim); margin-bottom: 4px; border-left: 2px solid transparent; }
.nav-item .tag{ font-family:'JetBrains Mono'; font-size:10px; opacity:0.6; margin-left:auto; }
.nav-item:hover{ background: var(--sidebar-active); }
.nav-item.active{ background: var(--sidebar-active); color: var(--sidebar-text); border-left-color: var(--gold); }

.sidebar-foot{ margin-top:auto; padding-top:20px; border-top:1px solid var(--sidebar-active); }
.who{ font-size:13px; color: var(--sidebar-text-dim); margin-bottom:10px; }
.who b{ color: var(--sidebar-text); }

.main{ padding: 36px 44px; overflow-y:auto; }
.page{ display:none; max-width: 980px; }
.page.active{ display:block; }

.page-head{ display:flex; align-items:flex-end; justify-content:space-between; margin-bottom: 26px; gap:20px; flex-wrap:wrap; }
.page-head h2{ font-size: 28px; margin:0 0 4px; }
.page-head .desc{ color: var(--text-muted); font-size:14px; max-width:480px; }

.grid{ display:grid; grid-template-columns: repeat(auto-fill, minmax(230px, 1fr)); gap: 18px; margin-bottom: 28px; }
.card{ background: var(--surface); border:1px solid var(--line); border-radius:3px; padding: 18px 16px 16px; position:relative; transition: transform .15s ease, box-shadow .15s ease; }
.card:hover{ transform: translateY(-2px); box-shadow: 0 14px 24px -16px rgba(32,40,60,0.35); }
.card::after{ content:""; position:absolute; left:0; right:0; bottom:0; height:4px; background: var(--sage); border-radius: 0 0 3px 3px; }
.card.cat-arbeit::after{ background: var(--rust); }
.card.cat-freizeit::after{ background: var(--gold); }
.card.cat-tools::after{ background: var(--sage); }

.card-top{ display:flex; justify-content:space-between; align-items:flex-start; margin-bottom:10px; }
.favicon{ width:30px; height:30px; border-radius:50%; background: var(--sidebar-bg); color: var(--sidebar-text); display:flex; align-items:center; justify-content:center; font-family: var(--font-display); font-weight:700; font-size:14px; flex-shrink:0; }
.card-cat{ font-family:'JetBrains Mono'; font-size:10px; text-transform:uppercase; letter-spacing:0.08em; color: var(--text-muted); }
.card h3{ font-size:16px; margin:0 0 4px; }
.card .url{ font-family:'JetBrains Mono'; font-size:11px; color: var(--text-muted); word-break:break-all; margin-bottom:14px; }
.card-actions{ display:flex; gap:8px; flex-wrap:wrap; }

.add-card{ border: 1.5px dashed var(--line); background: transparent; border-radius:3px; display:flex; align-items:center; justify-content:center; flex-direction:column; gap:6px; cursor:pointer; min-height: 138px; color: var(--text-muted); font-size:13px; }
.add-card:hover{ border-color: var(--sidebar-bg); color: var(--text); }
.add-card .plus{ font-family: var(--font-display); font-size:26px; line-height:1; }

.empty{ border:1px dashed var(--line); border-radius:4px; padding: 40px 24px; text-align:center; color: var(--text-muted); font-size:14px; margin-bottom:24px; }

.panel{ background: var(--surface); border:1px solid var(--line); border-radius:4px; padding: 24px; margin-bottom: 24px; }
.panel h3{ margin:0 0 4px; font-size:17px; }
.panel .hint{ font-size:13px; color: var(--text-muted); margin-bottom:14px; }
.row2{ display:grid; grid-template-columns: 1fr 1fr; gap: 14px; }
.select{ width:100%; padding:11px 12px; border:1px solid var(--line); border-bottom:2px solid var(--sidebar-bg); border-radius:2px; background: var(--surface-2); font-family: var(--font-body); font-size:15px; color: var(--text); }
textarea{ width:100%; padding:11px 12px; border:1px solid var(--line); border-bottom:2px solid var(--sidebar-bg); border-radius:2px; background: var(--surface-2); font-family: var(--font-body); font-size:14px; resize:vertical; min-height:90px; color: var(--text); }

/* settings tabs */
.settings-tabs{ display:flex; gap:6px; margin-bottom:22px; border-bottom:1px solid var(--line); }
.settings-tab{ border:none; background:transparent; cursor:pointer; padding: 10px 4px; margin-right:18px; font-family: var(--font-body); font-size:14px; font-weight:600; color: var(--text-muted); border-bottom: 2px solid transparent; }
.settings-tab.active{ color: var(--text); border-bottom-color: var(--gold); }
.settings-page{ display:none; }
.settings-page.active{ display:block; }

.option-group{ display:flex; flex-direction:column; gap:10px; }
.option-row{ display:flex; align-items:center; gap:12px; padding:12px 14px; border:1px solid var(--line); border-radius:4px; cursor:pointer; background: var(--surface-2); }
.option-row input{ accent-color: var(--gold); }
.option-row.active{ border-color: var(--gold); }
.option-row .label{ font-size:14px; font-weight:600; }
.swatch-row{ display:flex; gap:6px; margin-left:auto; }
.swatch{ width:14px; height:14px; border-radius:50%; border:1px solid rgba(0,0,0,0.15); }

/* viewer overlay */
#viewer{ position:fixed; inset:0; background: rgba(20,20,28,0.6); display:none; align-items:center; justify-content:center; padding: 28px; z-index: 50; }
.viewer-box{ background:#fff; width:100%; height:100%; max-width: 1180px; border-radius:6px; overflow:hidden; display:flex; flex-direction:column; box-shadow: 0 30px 60px -20px rgba(0,0,0,0.5); }
.viewer-bar{ display:flex; align-items:center; gap:12px; padding: 10px 14px; background: var(--sidebar-bg); color: var(--sidebar-text); }
.viewer-bar .url{ font-family:'JetBrains Mono'; font-size:12px; color: var(--sidebar-text-dim); flex:1; overflow:hidden; text-overflow:ellipsis; white-space:nowrap; }
.viewer-bar button{ background:none; border:none; color: var(--sidebar-text); cursor:pointer; font-size:13px; }
.viewer-note{ font-size:11px; color: rgba(32,40,60,0.65); padding:6px 14px; background:#EFE9DA; border-bottom:1px solid var(--line); }
.viewer-box iframe{ flex:1; border:none; }

.feedback-item{ border-left: 2px solid var(--gold); padding: 10px 0 10px 14px; margin-bottom: 10px; }
.feedback-item .meta{ font-family:'JetBrains Mono'; font-size:11px; color: var(--text-muted); margin-bottom:3px; }
.feedback-item .txt{ font-size:14px; }

.toast{ position:fixed; bottom:24px; right:24px; background: var(--sidebar-bg); color: var(--sidebar-text); padding: 12px 18px; border-radius:4px; font-size:14px; box-shadow:0 10px 24px rgba(0,0,0,0.25); opacity:0; transform: translateY(8px); transition: all .25s ease; pointer-events:none; z-index:90; }
.toast.show{ opacity:1; transform: translateY(0); }

@media (max-width: 720px){
  .shell{ grid-template-columns: 1fr; }
  .sidebar{ flex-direction:row; align-items:center; padding:14px 18px; overflow-x:auto; }
  .brand,.brand-sub,.sidebar-foot{ display:none; }
  .nav-item{ white-space:nowrap; }
  .main{ padding: 22px; }
  .row2{ grid-template-columns: 1fr; }
  #lang-switch{ top:auto; bottom:16px; right:16px; }
}
</style>
</head>
<body data-theme="papier" data-font="fraunces">

<div id="lang-switch">
  <button data-lang="de" onclick="setLang('de')">DE</button>
  <button data-lang="en" onclick="setLang('en')">EN</button>
  <button data-lang="es" onclick="setLang('es')">ES</button>
</div>

<!-- AUTH -->
<div id="screen-auth">
  <div class="passport">
    <div class="passport-inner">
      <div class="eyebrow" data-i18n="auth.eyebrow"></div>
      <h1 data-i18n="auth.headline"></h1>
      <div class="sub" data-i18n="auth.sub"></div>

      <div class="auth-toggle">
        <button id="tab-login" class="active" onclick="setAuthMode('login')" data-i18n="auth.tabLogin"></button>
        <button id="tab-register" onclick="setAuthMode('register')" data-i18n="auth.tabRegister"></button>
      </div>

      <div class="field">
        <label data-i18n="auth.nameLabel"></label>
        <input id="auth-user" type="text" autocomplete="username" data-i18n-placeholder="auth.namePlaceholder">
      </div>
      <div class="field">
        <label data-i18n="auth.passLabel"></label>
        <input id="auth-pass" type="password" autocomplete="current-password" placeholder="••••••••">
      </div>

      <button class="btn btn-primary" id="auth-submit" onclick="handleAuth()" data-i18n="auth.enterBtn"></button>
      <div class="auth-msg" id="auth-msg"></div>
    </div>
    <div class="stamp" data-i18n="auth.stamp"></div>
  </div>
</div>

<!-- APP -->
<div id="screen-app">
  <div class="shell">
    <div class="sidebar">
      <div class="brand">Atlas</div>
      <div class="brand-sub" data-i18n="nav.brandSub"></div>

      <div class="nav-item active" data-page="atlas" onclick="showPage('atlas')">
        <span data-i18n="nav.atlas"></span><span class="tag" id="nav-count">0</span>
      </div>
      <div class="nav-item" data-page="settings" onclick="showPage('settings')">
        <span data-i18n="nav.settings"></span>
      </div>

      <div class="sidebar-foot">
        <div class="who"><span data-i18n="nav.who"></span><br><b id="who-name">—</b></div>
        <button class="btn btn-ghost btn-small" onclick="logout()" style="width:100%;" data-i18n="nav.logout"></button>
      </div>
    </div>

    <div class="main">
      <!-- ATLAS PAGE -->
      <div class="page active" id="page-atlas">
        <div class="page-head">
          <div>
            <h2 data-i18n="atlas.title"></h2>
            <div class="desc" data-i18n="atlas.desc"></div>
          </div>
        </div>
        <div id="atlas-empty" class="empty" style="display:none;" data-i18n="atlas.empty"></div>
        <div class="grid" id="atlas-grid"></div>
      </div>

      <!-- SETTINGS PAGE -->
      <div class="page" id="page-settings">
        <div class="page-head">
          <div>
            <h2 data-i18n="settings.title"></h2>
            <div class="desc" data-i18n="settings.desc"></div>
          </div>
        </div>

        <div class="settings-tabs">
          <button class="settings-tab active" data-tab="account" onclick="showSettingsTab('account')" data-i18n="settings.tabAccount"></button>
          <button class="settings-tab" data-tab="appearance" onclick="showSettingsTab('appearance')" data-i18n="settings.tabAppearance"></button>
          <button class="settings-tab" data-tab="feedback" onclick="showSettingsTab('feedback')" data-i18n="settings.tabFeedback"></button>
        </div>

        <!-- ACCOUNT -->
        <div class="settings-page active" id="settings-account">
          <div class="panel">
            <h3 data-i18n="settings.passTitle"></h3>
            <div class="hint" data-i18n="settings.passHint"></div>
            <div class="row2">
              <div class="field" style="margin-bottom:0;">
                <label data-i18n="settings.newPass"></label>
                <input type="password" id="newpass">
              </div>
              <div class="field" style="margin-bottom:0;">
                <label data-i18n="settings.repeatPass"></label>
                <input type="password" id="newpass2">
              </div>
            </div>
            <div style="margin-top:14px; display:flex; align-items:center; gap:14px;">
              <button class="btn btn-primary btn-small" onclick="changePassword()" data-i18n="settings.save"></button>
              <span class="auth-msg" id="pass-msg" style="margin:0;"></span>
            </div>
          </div>
        </div>

        <!-- APPEARANCE -->
        <div class="settings-page" id="settings-appearance">
          <div class="panel">
            <h3 data-i18n="settings.fontTitle"></h3>
            <div class="hint" data-i18n="settings.fontHint"></div>
            <div class="option-group" id="font-options"></div>
          </div>
          <div class="panel">
            <h3 data-i18n="settings.themeTitle"></h3>
            <div class="hint" data-i18n="settings.themeHint"></div>
            <div class="option-group" id="theme-options"></div>
          </div>
        </div>

        <!-- FEEDBACK -->
        <div class="settings-page" id="settings-feedback">
          <div class="panel">
            <h3 data-i18n="settings.fbTitle"></h3>
            <div class="hint" data-i18n="settings.fbHint"></div>
            <div class="row2" style="margin-bottom:12px;">
              <div class="field" style="margin-bottom:0;">
                <label data-i18n="fb.name"></label>
                <input type="text" id="fb-name" placeholder="Are.na">
              </div>
              <div class="field" style="margin-bottom:0;">
                <label data-i18n="fb.url"></label>
                <input type="text" id="fb-url" placeholder="are.na">
              </div>
            </div>
            <div class="field" style="margin-bottom:14px;">
              <label data-i18n="fb.why"></label>
              <textarea id="fb-text"></textarea>
            </div>
            <button class="btn btn-primary btn-small" onclick="submitFeedback()" data-i18n="fb.submit"></button>
            <span class="auth-msg" id="fb-msg" style="margin-left:12px;"></span>
          </div>

          <div>
            <h3 data-i18n="settings.fbListTitle"></h3>
            <div class="hint" data-i18n="settings.fbListHint"></div>
            <div id="feedback-list"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- VIEWER -->
<div id="viewer">
  <div class="viewer-box">
    <div class="viewer-bar">
      <span class="url" id="viewer-url"></span>
      <button onclick="closeViewer()" data-i18n="viewer.close"></button>
    </div>
    <div class="viewer-note" data-i18n="viewer.note"></div>
    <iframe id="viewer-frame" src=""></iframe>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
/* ---------------- i18n ---------------- */
const T = {
  'auth.eyebrow': {de:'Zugang · Atlas', en:'Access · Atlas', es:'Acceso · Atlas'},
  'auth.headline': {de:'Dein eigener Atlas.', en:'Your own atlas.', es:'Tu propio atlas.'},
  'auth.sub': {de:'Trag dich ein, dann öffnet sich dein Logbuch.', en:'Sign in and your logbook opens.', es:'Regístrate y se abre tu cuaderno.'},
  'auth.tabLogin': {de:'Anmelden', en:'Sign in', es:'Iniciar sesión'},
  'auth.tabRegister': {de:'Neu eintragen', en:'Register', es:'Registrarse'},
  'auth.nameLabel': {de:'Name', en:'Name', es:'Nombre'},
  'auth.namePlaceholder': {de:'z. B. lena', en:'e.g. lena', es:'p. ej. lena'},
  'auth.passLabel': {de:'Passwort', en:'Password', es:'Contraseña'},
  'auth.enterBtn': {de:'Eintreten', en:'Enter', es:'Entrar'},
  'auth.registerBtn': {de:'Konto anlegen', en:'Create account', es:'Crear cuenta'},
  'auth.stamp': {de:'EINGE-<br>TRAGEN<br>SEIT 2026', en:'REGIS-<br>TERED<br>SINCE 2026', es:'REGIS-<br>TRADO<br>DESDE 2026'},
  'nav.brandSub': {de:'Logbuch deiner Seiten', en:'Logbook of your sites', es:'Cuaderno de tus sitios'},
  'nav.atlas': {de:'Karteikasten', en:'Index cards', es:'Fichero'},
  'nav.settings': {de:'Einstellungen', en:'Settings', es:'Ajustes'},
  'nav.who': {de:'Eingetragen als', en:'Signed in as', es:'Conectado como'},
  'nav.logout': {de:'Austragen', en:'Sign out', es:'Salir'},
  'atlas.title': {de:'Dein Karteikasten', en:'Your index cards', es:'Tu fichero'},
  'atlas.desc': {de:'Seiten, die du gerade verwaltest. Karte anklicken öffnet sie direkt hier drin.', en:'Sites you currently manage. Click a card to open it right here.', es:'Sitios que gestionas ahora. Haz clic en una tarjeta para abrirla aquí mismo.'},
  'atlas.empty': {de:'Noch keine Seite eingetragen. Leg unten die erste Karte an.', en:'No site yet. Add the first card below.', es:'Todavía no hay ningún sitio. Crea la primera tarjeta abajo.'},
  'atlas.open': {de:'Öffnen', en:'Open', es:'Abrir'},
  'atlas.newTab': {de:'Neuer Tab', en:'New tab', es:'Nueva pestaña'},
  'atlas.remove': {de:'Entfernen', en:'Remove', es:'Quitar'},
  'atlas.addCard': {de:'Neue Seite eintragen', en:'Add a new site', es:'Añadir un sitio'},
  'atlas.newCardTitle': {de:'Neue Karte', en:'New card', es:'Nueva tarjeta'},
  'atlas.fieldName': {de:'Name', en:'Name', es:'Nombre'},
  'atlas.fieldUrl': {de:'Adresse', en:'Address', es:'Dirección'},
  'atlas.fieldCategory': {de:'Kategorie', en:'Category', es:'Categoría'},
  'cat.arbeit': {de:'Arbeit', en:'Work', es:'Trabajo'},
  'cat.freizeit': {de:'Freizeit', en:'Leisure', es:'Ocio'},
  'cat.tools': {de:'Werkzeug', en:'Tool', es:'Herramienta'},
  'atlas.saveCard': {de:'Karte anlegen', en:'Create card', es:'Crear tarjeta'},
  'atlas.cancel': {de:'Abbrechen', en:'Cancel', es:'Cancelar'},
  'atlas.fillBoth': {de:'Name und Adresse ausfüllen.', en:'Fill in name and address.', es:'Completa nombre y dirección.'},
  'atlas.cardCreated': {de:'Karte angelegt.', en:'Card created.', es:'Tarjeta creada.'},
  'viewer.close': {de:'Schließen ✕', en:'Close ✕', es:'Cerrar ✕'},
  'viewer.note': {de:'Manche Seiten lassen sich aus Sicherheitsgründen nicht einbetten — nutz dann "Neuer Tab" auf der Karte.', en:'Some sites refuse to be embedded for security reasons — use "New tab" on the card instead.', es:'Algunos sitios no permiten incrustarse por seguridad — usa "Nueva pestaña" en la tarjeta.'},
  'settings.title': {de:'Einstellungen', en:'Settings', es:'Ajustes'},
  'settings.desc': {de:'Konto und Darstellung anpassen — oder eine Seite für den Atlas vorschlagen.', en:'Adjust account and appearance — or suggest a site for the atlas.', es:'Ajusta tu cuenta y apariencia — o propone un sitio para el atlas.'},
  'settings.tabAccount': {de:'Konto', en:'Account', es:'Cuenta'},
  'settings.tabAppearance': {de:'Darstellung', en:'Appearance', es:'Apariencia'},
  'settings.tabFeedback': {de:'Feedback', en:'Feedback', es:'Comentarios'},
  'settings.passTitle': {de:'Passwort ändern', en:'Change password', es:'Cambiar contraseña'},
  'settings.passHint': {de:'Wirkt sofort, gilt für die nächste Anmeldung.', en:'Applies immediately, for your next sign-in.', es:'Se aplica de inmediato, válido desde el próximo inicio de sesión.'},
  'settings.newPass': {de:'Neues Passwort', en:'New password', es:'Nueva contraseña'},
  'settings.repeatPass': {de:'Wiederholen', en:'Repeat', es:'Repetir'},
  'settings.save': {de:'Speichern', en:'Save', es:'Guardar'},
  'pass.tooShort': {de:'Mindestens 4 Zeichen.', en:'At least 4 characters.', es:'Al menos 4 caracteres.'},
  'pass.mismatch': {de:'Stimmt nicht überein.', en:'Does not match.', es:'No coincide.'},
  'pass.saved': {de:'Gespeichert.', en:'Saved.', es:'Guardado.'},
  'settings.fontTitle': {de:'Schrift', en:'Font', es:'Tipografía'},
  'settings.fontHint': {de:'Ändert Überschriften und Text im ganzen Atlas.', en:'Changes headings and text across the whole atlas.', es:'Cambia los títulos y el texto en todo el atlas.'},
  'font.fraunces': {de:'Fraunces / Source Sans — Standard', en:'Fraunces / Source Sans — default', es:'Fraunces / Source Sans — por defecto'},
  'font.mono': {de:'JetBrains Mono — technisch', en:'JetBrains Mono — technical', es:'JetBrains Mono — técnica'},
  'font.klassisch': {de:'Georgia / Helvetica — klassisch', en:'Georgia / Helvetica — classic', es:'Georgia / Helvetica — clásica'},
  'settings.themeTitle': {de:'Thema', en:'Theme', es:'Tema'},
  'settings.themeHint': {de:'Helligkeit und Farbwelt des Atlas.', en:'Brightness and color world of the atlas.', es:'Brillo y paleta de color del atlas.'},
  'theme.papier': {de:'Papier — hell', en:'Paper — light', es:'Papel — claro'},
  'theme.nacht': {de:'Nacht — dunkel', en:'Night — dark', es:'Noche — oscuro'},
  'theme.kontrast': {de:'Kontrast — scharf', en:'Contrast — sharp', es:'Contraste — nítido'},
  'fb.name': {de:'Name', en:'Name', es:'Nombre'},
  'fb.url': {de:'Adresse', en:'Address', es:'Dirección'},
  'fb.why': {de:'Warum gehört sie rein?', en:'Why does it belong?', es:'¿Por qué debería estar?'},
  'fb.submit': {de:'Vorschlag einreichen', en:'Submit suggestion', es:'Enviar propuesta'},
  'fb.fillReq': {de:'Name und Begründung ausfüllen.', en:'Fill in name and reason.', es:'Completa nombre y motivo.'},
  'fb.submitted': {de:'Eingereicht.', en:'Submitted.', es:'Enviado.'},
  'fb.failed': {de:'Fehlgeschlagen, nochmal versuchen.', en:'Failed, try again.', es:'Falló, inténtalo de nuevo.'},
  'fb.by': {de:'vorgeschlagen von', en:'suggested by', es:'propuesto por'},
  'settings.fbTitle': {de:'Website vorschlagen', en:'Suggest a website', es:'Proponer un sitio'},
  'settings.fbHint': {de:'Dein Vorschlag landet in der gemeinsamen Liste — sichtbar für alle, die hier eingetragen sind.', en:'Your suggestion goes into the shared list — visible to everyone registered here.', es:'Tu propuesta entra en la lista compartida — visible para todos los registrados aquí.'},
  'settings.fbListTitle': {de:'Vorschläge der Runde', en:'Suggestions so far', es:'Propuestas hasta ahora'},
  'settings.fbListHint': {de:'Was andere bisher eingereicht haben.', en:'What others have submitted so far.', es:'Lo que otros han propuesto hasta ahora.'},
  'fb.loading': {de:'Lade …', en:'Loading …', es:'Cargando …'},
  'fb.none': {de:'Noch nichts eingereicht.', en:'Nothing submitted yet.', es:'Todavía no hay nada.'},
  'fb.loadFail': {de:'Konnte nicht geladen werden.', en:'Could not load.', es:'No se pudo cargar.'},
  'toast.saveFail': {de:'Speichern fehlgeschlagen — nochmal versuchen.', en:'Save failed — try again.', es:'Error al guardar — inténtalo de nuevo.'},
  'auth.fillBoth': {de:'Name und Passwort ausfüllen.', en:'Fill in name and password.', es:'Completa nombre y contraseña.'},
  'auth.nameFormat': {de:'Name: nur Buchstaben/Zahlen, 2-24 Zeichen.', en:'Name: letters/numbers only, 2-24 characters.', es:'Nombre: solo letras/números, 2-24 caracteres.'},
  'auth.loading': {de:'Einen Moment …', en:'One moment …', es:'Un momento …'},
  'auth.exists': {de:'Diesen Namen gibt es schon. Anmelden statt anlegen.', en:'That name is taken. Sign in instead of registering.', es:'Ese nombre ya existe. Inicia sesión en vez de registrarte.'},
  'auth.saveFail': {de:'Konnte nicht gespeichert werden. Nochmal versuchen.', en:'Could not save. Try again.', es:'No se pudo guardar. Inténtalo de nuevo.'},
  'auth.backendDown': {de:'Speicher antwortet gerade nicht. Kurz warten und nochmal.', en:'Storage is not responding right now. Wait a moment and retry.', es:'El almacenamiento no responde ahora. Espera un momento e inténtalo de nuevo.'},
  'auth.unknownOrDown': {de:'Unbekannter Name oder Speicher antwortet nicht.', en:'Unknown name or storage not responding.', es:'Nombre desconocido o el almacenamiento no responde.'},
  'auth.wrongPass': {de:'Passwort stimmt nicht.', en:'Wrong password.', es:'Contraseña incorrecta.'},
  'auth.generic': {de:'Etwas ist schiefgelaufen. Nochmal versuchen.', en:'Something went wrong. Try again.', es:'Algo salió mal. Inténtalo de nuevo.'},
};
function t(key){ return (T[key] && T[key][currentLang]) || key; }

let currentLang = 'de';
let currentFont = 'fraunces';
let currentTheme = 'papier';
let authMode = 'login';
let currentUser = null;
let userData = null;

const FONT_OPTIONS = ['fraunces','mono','klassisch'];
const THEME_OPTIONS = ['papier','nacht','kontrast'];

function showToast(msg){
  const el = document.getElementById('toast');
  el.textContent = msg; el.classList.add('show');
  setTimeout(()=>el.classList.remove('show'), 2400);
}

async function sha256(text){
  const buf = await crypto.subtle.digest('SHA-256', new TextEncoder().encode(text));
  return Array.from(new Uint8Array(buf)).map(b=>b.toString(16).padStart(2,'0')).join('');
}

async function storageSet(key, value, shared, retries=2){
  for(let a=0; a<=retries; a++){
    try{ const res = await window.storage.set(key, value, shared); if(res) return res; }
    catch(e){ if(a===retries) throw e; }
    await new Promise(r=>setTimeout(r, 400*(a+1)));
  }
  return null;
}
async function storageGet(key, shared, retries=2){
  for(let a=0; a<=retries; a++){
    try{ return await window.storage.get(key, shared); }
    catch(e){ if(a===retries) throw e; }
    await new Promise(r=>setTimeout(r, 400*(a+1)));
  }
}

/* ---------------- language / font / theme ---------------- */
function setLang(lang){
  currentLang = lang;
  document.querySelectorAll('#lang-switch button').forEach(b=>b.classList.toggle('active', b.dataset.lang===lang));
  translateUI();
  if(currentUser) persistPrefs();
}

function setFont(font){
  currentFont = font;
  document.body.dataset.font = font;
  renderFontOptions();
  if(currentUser) persistPrefs();
}

function setTheme(theme){
  currentTheme = theme;
  document.body.dataset.theme = theme;
  renderThemeOptions();
  if(currentUser) persistPrefs();
}

async function persistPrefs(){
  userData.prefs = { lang: currentLang, font: currentFont, theme: currentTheme };
  await persistUser();
}

function translateUI(){
  document.querySelectorAll('[data-i18n]').forEach(el=>{ el.innerHTML = t(el.dataset.i18n); });
  document.querySelectorAll('[data-i18n-placeholder]').forEach(el=>{ el.placeholder = t(el.dataset.i18nPlaceholder); });
  document.getElementById('auth-submit').textContent = authMode==='login' ? t('auth.enterBtn') : t('auth.registerBtn');
  if(currentUser){ renderSites(); renderFontOptions(); renderThemeOptions(); loadFeedback(); }
}

function renderFontOptions(){
  const wrap = document.getElementById('font-options');
  if(!wrap) return;
  wrap.innerHTML = '';
  FONT_OPTIONS.forEach(f=>{
    const row = document.createElement('label');
    row.className = 'option-row' + (currentFont===f ? ' active' : '');
    row.innerHTML = `<input type="radio" name="font-opt" ${currentFont===f?'checked':''}><span class="label">${t('font.'+f)}</span>`;
    row.onclick = ()=>setFont(f);
    wrap.appendChild(row);
  });
}

function renderThemeOptions(){
  const wrap = document.getElementById('theme-options');
  if(!wrap) return;
  const swatches = { papier:['#EDE6D6','#20283C','#B5482E'], nacht:['#161A26','#EDE6D6','#D4684A'], kontrast:['#FFFFFF','#000000','#B5482E'] };
  wrap.innerHTML = '';
  THEME_OPTIONS.forEach(th=>{
    const row = document.createElement('label');
    row.className = 'option-row' + (currentTheme===th ? ' active' : '');
    const sw = swatches[th].map(c=>`<span class="swatch" style="background:${c}"></span>`).join('');
    row.innerHTML = `<input type="radio" name="theme-opt" ${currentTheme===th?'checked':''}><span class="label">${t('theme.'+th)}</span><span class="swatch-row">${sw}</span>`;
    row.onclick = ()=>setTheme(th);
    wrap.appendChild(row);
  });
}

/* ---------------- auth ---------------- */
function setAuthMode(mode){
  authMode = mode;
  document.getElementById('tab-login').classList.toggle('active', mode==='login');
  document.getElementById('tab-register').classList.toggle('active', mode==='register');
  document.getElementById('auth-submit').textContent = mode==='login' ? t('auth.enterBtn') : t('auth.registerBtn');
  document.getElementById('auth-msg').textContent = '';
}

function setMsg(id, text, kind){
  const el = document.getElementById(id);
  el.textContent = text; el.className = 'auth-msg' + (kind ? ' '+kind : '');
}

async function handleAuth(){
  const user = document.getElementById('auth-user').value.trim().toLowerCase();
  const pass = document.getElementById('auth-pass').value;
  if(!user || !pass){ setMsg('auth-msg', t('auth.fillBoth'), 'error'); return; }
  if(!/^[a-z0-9_\-]{2,24}$/.test(user)){ setMsg('auth-msg', t('auth.nameFormat'), 'error'); return; }

  setMsg('auth-msg', t('auth.loading'), '');
  const hash = await sha256(pass);
  const key = 'user:'+user;

  try{
    if(authMode === 'register'){
      let exists = true;
      try{ await storageGet(key, true); }catch(e){ exists = false; }
      if(exists){ setMsg('auth-msg', t('auth.exists'), 'error'); return; }
      const fresh = { passwordHash: hash, sites: [], createdAt: Date.now(), prefs: { lang: currentLang, font: 'fraunces', theme: 'papier' } };
      let res;
      try{ res = await storageSet(key, JSON.stringify(fresh), true); }
      catch(e){ setMsg('auth-msg', t('auth.backendDown'), 'error'); return; }
      if(!res){ setMsg('auth-msg', t('auth.saveFail'), 'error'); return; }
      currentUser = user; userData = fresh;
      enterApp();
    } else {
      let raw;
      try{ raw = await storageGet(key, true); }
      catch(e){ setMsg('auth-msg', t('auth.unknownOrDown'), 'error'); return; }
      const data = JSON.parse(raw.value);
      if(data.passwordHash !== hash){ setMsg('auth-msg', t('auth.wrongPass'), 'error'); return; }
      currentUser = user; userData = data;
      enterApp();
    }
  }catch(err){
    setMsg('auth-msg', t('auth.generic'), 'error');
    console.error(err);
  }
}

function logout(){
  currentUser = null; userData = null;
  document.getElementById('screen-app').style.display = 'none';
  document.getElementById('screen-auth').style.display = 'flex';
  document.getElementById('auth-pass').value = '';
}

async function enterApp(){
  const prefs = userData.prefs || { lang:'de', font:'fraunces', theme:'papier' };
  currentLang = prefs.lang || 'de';
  currentFont = prefs.font || 'fraunces';
  currentTheme = prefs.theme || 'papier';
  document.body.dataset.font = currentFont;
  document.body.dataset.theme = currentTheme;
  document.querySelectorAll('#lang-switch button').forEach(b=>b.classList.toggle('active', b.dataset.lang===currentLang));

  document.getElementById('screen-auth').style.display = 'none';
  document.getElementById('screen-app').style.display = 'block';
  document.getElementById('who-name').textContent = currentUser;

  translateUI();
  renderSites();
  renderFontOptions();
  renderThemeOptions();
  showPage('atlas');
  showSettingsTab('account');
  loadFeedback();
}

function showPage(name){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
  document.getElementById('page-'+name).classList.add('active');
  document.querySelector('.nav-item[data-page="'+name+'"]').classList.add('active');
}

function showSettingsTab(name){
  document.querySelectorAll('.settings-page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.settings-tab').forEach(b=>b.classList.remove('active'));
  document.getElementById('settings-'+name).classList.add('active');
  document.querySelector('.settings-tab[data-tab="'+name+'"]').classList.add('active');
}

async function persistUser(){
  const key = 'user:'+currentUser;
  try{
    const res = await storageSet(key, JSON.stringify(userData), true);
    if(!res) showToast(t('toast.saveFail'));
  }catch(e){ showToast(t('toast.saveFail')); console.error(e); }
}

/* ---------------- atlas ---------------- */
function renderSites(){
  const grid = document.getElementById('atlas-grid');
  const empty = document.getElementById('atlas-empty');
  document.getElementById('nav-count').textContent = userData.sites.length;
  empty.style.display = userData.sites.length ? 'none' : 'block';

  grid.innerHTML = '';
  userData.sites.forEach((site, idx)=>{
    const card = document.createElement('div');
    card.className = 'card cat-'+site.cat;
    const initial = (site.name||'?').trim().charAt(0).toUpperCase();
    card.innerHTML = `
      <div class="card-top">
        <div class="favicon">${initial}</div>
        <div class="card-cat">${t('cat.'+site.cat) || site.cat}</div>
      </div>
      <h3>${escapeHtml(site.name)}</h3>
      <div class="url">${escapeHtml(site.url)}</div>
      <div class="card-actions">
        <button class="btn btn-ghost btn-small" onclick="openSite(${idx})">${t('atlas.open')}</button>
        <button class="btn btn-ghost btn-small" onclick="window.open(normalizeUrl('${site.url.replace(/'/g,"")}'), '_blank')">${t('atlas.newTab')}</button>
        <button class="btn-danger-text" onclick="removeSite(${idx})">${t('atlas.remove')}</button>
      </div>
    `;
    grid.appendChild(card);
  });

  const addCard = document.createElement('div');
  addCard.className = 'add-card';
  addCard.onclick = openAddForm;
  addCard.innerHTML = `<div class="plus">+</div><div>${t('atlas.addCard')}</div>`;
  grid.appendChild(addCard);
}

function escapeHtml(s){ return (s||'').replace(/[&<>"']/g, c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c])); }
function normalizeUrl(u){ return /^https?:\/\//i.test(u) ? u : 'https://'+u; }

function openAddForm(){
  if(document.getElementById('add-panel')) return;
  const panel = document.createElement('div');
  panel.className = 'panel';
  panel.id = 'add-panel';
  panel.innerHTML = `
    <h3>${t('atlas.newCardTitle')}</h3>
    <div class="row2" style="margin-bottom:14px;">
      <div class="field" style="margin-bottom:0;">
        <label>${t('atlas.fieldName')}</label>
        <input type="text" id="new-name">
      </div>
      <div class="field" style="margin-bottom:0;">
        <label>${t('atlas.fieldUrl')}</label>
        <input type="text" id="new-url">
      </div>
    </div>
    <div class="field" style="margin-bottom:14px;">
      <label>${t('atlas.fieldCategory')}</label>
      <select class="select" id="new-cat">
        <option value="arbeit">${t('cat.arbeit')}</option>
        <option value="freizeit">${t('cat.freizeit')}</option>
        <option value="tools">${t('cat.tools')}</option>
      </select>
    </div>
    <div style="display:flex; gap:10px;">
      <button class="btn btn-primary btn-small" onclick="saveNewSite()">${t('atlas.saveCard')}</button>
      <button class="btn btn-ghost btn-small" onclick="document.getElementById('add-panel').remove()">${t('atlas.cancel')}</button>
    </div>
  `;
  document.getElementById('atlas-grid').before(panel);
  document.getElementById('new-name').focus();
}

async function saveNewSite(){
  const name = document.getElementById('new-name').value.trim();
  const url = document.getElementById('new-url').value.trim();
  const cat = document.getElementById('new-cat').value;
  if(!name || !url){ showToast(t('atlas.fillBoth')); return; }
  userData.sites.push({ name, url, cat, addedAt: Date.now() });
  document.getElementById('add-panel').remove();
  renderSites();
  await persistUser();
  showToast(t('atlas.cardCreated'));
}

async function removeSite(idx){
  userData.sites.splice(idx,1);
  renderSites();
  await persistUser();
}

function openSite(idx){
  const site = userData.sites[idx];
  document.getElementById('viewer-url').textContent = site.url;
  document.getElementById('viewer-frame').src = normalizeUrl(site.url);
  document.getElementById('viewer').style.display = 'flex';
}
function closeViewer(){
  document.getElementById('viewer').style.display = 'none';
  document.getElementById('viewer-frame').src = '';
}

/* ---------------- settings: account ---------------- */
async function changePassword(){
  const p1 = document.getElementById('newpass').value;
  const p2 = document.getElementById('newpass2').value;
  if(!p1 || p1.length < 4){ setMsg('pass-msg', t('pass.tooShort'), 'error'); return; }
  if(p1 !== p2){ setMsg('pass-msg', t('pass.mismatch'), 'error'); return; }
  userData.passwordHash = await sha256(p1);
  await persistUser();
  document.getElementById('newpass').value = '';
  document.getElementById('newpass2').value = '';
  setMsg('pass-msg', t('pass.saved'), 'ok');
}

/* ---------------- settings: feedback ---------------- */
async function submitFeedback(){
  const name = document.getElementById('fb-name').value.trim();
  const url = document.getElementById('fb-url').value.trim();
  const text = document.getElementById('fb-text').value.trim();
  if(!name || !text){ setMsg('fb-msg', t('fb.fillReq'), 'error'); return; }
  const id = 'feedback:'+Date.now()+'-'+Math.random().toString(36).slice(2,7);
  const entry = { name, url, text, by: currentUser, at: Date.now() };
  try{
    const res = await storageSet(id, JSON.stringify(entry), true);
    if(!res){ setMsg('fb-msg', t('fb.failed'), 'error'); return; }
    document.getElementById('fb-name').value='';
    document.getElementById('fb-url').value='';
    document.getElementById('fb-text').value='';
    setMsg('fb-msg', t('fb.submitted'), 'ok');
    loadFeedback();
  }catch(e){ setMsg('fb-msg', t('fb.failed'), 'error'); console.error(e); }
}

async function loadFeedback(){
  const list = document.getElementById('feedback-list');
  if(!list) return;
  list.innerHTML = `<div class="hint">${t('fb.loading')}</div>`;
  try{
    const res = await window.storage.list('feedback:', true);
    const keys = (res && res.keys) ? res.keys : [];
    if(!keys.length){ list.innerHTML = `<div class="hint">${t('fb.none')}</div>`; return; }

    const entries = [];
    for(const k of keys){
      try{ const item = await storageGet(k, true); entries.push(JSON.parse(item.value)); }catch(e){}
    }
    entries.sort((a,b)=> b.at - a.at);

    list.innerHTML = '';
    entries.forEach(e=>{
      const div = document.createElement('div');
      div.className = 'feedback-item';  
      const date = new Date(e.at).toLocaleDateString(currentLang==='de'?'de-DE':currentLang==='es'?'es-ES':'en-US');
      div.innerHTML = `
        <div class="meta">${escapeHtml(e.name)}${e.url ? ' · '+escapeHtml(e.url) : ''} · ${t('fb.by')} ${escapeHtml(e.by)} · ${date}</div>
        <div class="txt">${escapeHtml(e.text)}</div>
      `;
      list.appendChild(div);
    });
  }catch(e){
    list.innerHTML = `<div class="hint">${t('fb.loadFail')}</div>`;
    console.error(e);
  }
}

document.getElementById('auth-pass').addEventListener('keydown', e=>{ if(e.key==='Enter') handleAuth(); });
document.getElementById('auth-user').addEventListener('keydown', e=>{ if(e.key==='Enter') handleAuth(); });

translateUI();
</script>
</body>
</html>
