<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>عروض LUNA الشتوية</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap');

  :root {
    --bg: #fbf4ef;
    --card: #ffffff;
    --brown: #b08968;
    --brown-dark: #8a6648;
    --pink: #f4cdd5;
    --pink-soft: #fbe6ea;
    --black: #1b1613;
    --muted: #7d6b5d;
    --line: #ecdcd0;
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  body { font-family:'Cairo',sans-serif; background:var(--bg); color:var(--black); padding-bottom:84px; overflow-x:hidden; }
  body.locked { overflow:hidden; height:100vh; }

  /* ===== Gift intro ===== */
  #intro { position:fixed; inset:0; z-index:200; background:radial-gradient(circle at 50% 45%, var(--pink-soft), var(--pink)); display:flex; flex-direction:column; align-items:center; justify-content:center; transition:opacity .7s ease, visibility .7s; cursor:pointer; }
  #intro.hide { opacity:0; visibility:hidden; }
  .gift { position:relative; width:150px; height:150px; animation:giftShake 1s ease .3s 1; }
  .gift-body { position:absolute; bottom:0; left:0; width:150px; height:100px; background:var(--brown); border-radius:6px 6px 12px 12px; box-shadow:0 14px 30px rgba(138,102,72,.35); }
  .gift-body::before { content:""; position:absolute; top:0; bottom:0; left:50%; width:26px; margin-left:-13px; background:var(--pink-soft); }
  .gift-lid { position:absolute; top:12px; left:-8px; width:166px; height:40px; background:var(--brown-dark); border-radius:8px; transform-origin:100% 100%; animation:lidOpen .9s cubic-bezier(.3,1.4,.5,1) 1.5s forwards; z-index:2; }
  .gift-lid::before { content:""; position:absolute; top:0; bottom:0; left:50%; width:26px; margin-left:-13px; background:var(--pink); }
  .gift-lid::after { content:""; position:absolute; top:-22px; left:50%; width:44px; height:28px; margin-left:-22px; border:8px solid var(--pink); border-radius:50% 50% 0 0; border-bottom:none; }
  .spark { position:absolute; top:40px; left:50%; font-size:22px; opacity:0; animation:spark 1.3s ease-out 1.7s forwards; }
  .spark:nth-child(1){ --x:-90px; --y:-120px; } .spark:nth-child(2){ --x:0px; --y:-150px; } .spark:nth-child(3){ --x:90px; --y:-120px; }
  .spark:nth-child(4){ --x:-55px; --y:-70px; } .spark:nth-child(5){ --x:55px; --y:-70px; }
  .intro-text { margin-top:34px; font-size:18px; font-weight:800; color:var(--brown-dark); opacity:0; animation:fadeIn .6s ease 1.9s forwards; }
  @keyframes giftShake { 0%,100%{transform:rotate(0)} 20%{transform:rotate(-6deg)} 40%{transform:rotate(6deg)} 60%{transform:rotate(-4deg)} 80%{transform:rotate(4deg)} }
  @keyframes lidOpen { to { transform:translate(-30px,-70px) rotate(-35deg); opacity:.0; } }
  @keyframes spark { 0%{opacity:0; transform:translate(0,0) scale(.4)} 30%{opacity:1} 100%{opacity:0; transform:translate(var(--x),var(--y)) scale(1.2)} }
  @keyframes fadeIn { to { opacity:1; } }

  /* ===== Hero ===== */
  .hero { text-align:center; padding:34px 16px 22px; background:linear-gradient(180deg,var(--pink-soft),var(--bg)); }
  .hero .moon { font-size:30px; }
  .hero h1 { font-size:clamp(26px,6vw,36px); font-weight:900; color:var(--black); margin:4px 0 6px; }
  .hero p { font-size:14px; color:var(--muted); }

  /* ===== Products ===== */
  .products { max-width:600px; margin:0 auto; padding:10px 14px 20px; display:flex; flex-direction:column; gap:22px; }
  .card { background:var(--card); border-radius:22px; padding:12px 12px 16px; border:2px solid var(--line); transition:.25s; }
  .card.in-cart { border-color:var(--brown); box-shadow:0 10px 28px rgba(176,137,104,.2); }
  .img-wrap { width:100%; aspect-ratio:1/1; border-radius:16px; overflow:hidden; background:var(--pink-soft); display:flex; align-items:center; justify-content:center; color:var(--brown); font-weight:700; margin-bottom:12px; }
  .img-wrap img { width:100%; height:100%; object-fit:cover; }
  .p-name { font-size:17px; font-weight:900; text-align:center; line-height:1.5; }
  .p-price { font-size:24px; font-weight:900; color:var(--brown-dark); text-align:center; margin:4px 0 12px; }

  .qty { display:flex; align-items:center; justify-content:space-between; background:var(--bg); border:1px solid var(--line); border-radius:14px; padding:6px 12px; margin-bottom:10px; }
  .qty button { width:38px; height:38px; border:none; border-radius:10px; background:var(--brown); color:#fff; font-size:22px; font-weight:900; cursor:pointer; }
  .qty button:active { transform:scale(.92); }
  .qty span { font-size:18px; font-weight:900; }

  .colors { background:var(--pink-soft); border-radius:14px; padding:12px; margin-bottom:10px; display:none; }
  .card.in-cart .colors { display:block; }
  .color-row + .color-row { margin-top:10px; }
  .color-label { font-size:13px; font-weight:800; color:var(--brown-dark); margin-bottom:6px; }
  .swatches { display:grid; grid-template-columns:1fr 1fr; gap:8px; }
  .swatch { display:flex; align-items:center; justify-content:center; gap:8px; padding:9px; border:2px solid var(--line); border-radius:12px; background:#fff; font-family:inherit; font-size:13px; font-weight:700; cursor:pointer; color:var(--black); }
  .swatch i { width:18px; height:18px; border-radius:50%; border:1px solid #cdb9a8; display:inline-block; }
  .swatch.active { border-color:var(--brown-dark); background:#fff; box-shadow:0 0 0 2px rgba(176,137,104,.3); }
  .swatch:focus-visible, .qty button:focus-visible, .buy:focus-visible { outline:3px solid var(--black); outline-offset:2px; }

  .buy { width:100%; padding:13px; border:none; border-radius:14px; background:var(--black); color:#fff; font-family:inherit; font-size:16px; font-weight:900; cursor:pointer; }

  /* ===== Floating bar ===== */
  .floating { position:fixed; bottom:0; right:0; left:0; z-index:50; display:none; align-items:center; justify-content:space-between; padding:12px 16px; background:#fff; border-top:2px solid var(--brown); box-shadow:0 -6px 22px rgba(0,0,0,.12); }
  .floating.visible { display:flex; }
  .floating .info { font-size:13px; color:var(--muted); }
  .floating .info b { color:var(--brown-dark); font-size:16px; }
  .floating button { background:var(--brown); color:#fff; border:none; border-radius:12px; padding:10px 20px; font-family:inherit; font-size:14px; font-weight:900; cursor:pointer; }

  /* ===== Order form ===== */
  .order-wrap { max-width:560px; margin:10px auto 40px; padding:0 14px; }
  .order { background:#fff; padding:24px 18px; border-radius:22px; border-top:5px solid var(--pink); box-shadow:0 12px 34px rgba(138,102,72,.15); }
  .order h3 { text-align:center; font-size:19px; font-weight:900; margin-bottom:16px; }
  .fg { margin-bottom:12px; }
  .fg label { display:block; font-size:13px; font-weight:700; color:var(--muted); margin-bottom:4px; }
  .fg input, .fg select { width:100%; padding:11px 12px; border:1.5px solid var(--line); border-radius:12px; font-family:inherit; font-size:14px; background:#fffdfb; outline:none; }
  .fg input:focus, .fg select:focus { border-color:var(--brown); }
  .cart-box { background:var(--bg); border:1px dashed var(--brown); border-radius:14px; padding:12px; margin-bottom:14px; }
  .cart-box .t { font-size:12px; font-weight:800; color:var(--brown-dark); margin-bottom:6px; }
  .line { display:flex; justify-content:space-between; gap:10px; font-size:13px; padding:6px 0; border-bottom:1px solid var(--line); }
  .line:last-child { border-bottom:none; }
  .line small { display:block; color:var(--muted); font-size:11px; margin-top:2px; }
  .empty { text-align:center; font-size:12px; color:var(--muted); }

  .del-grid { display:grid; grid-template-columns:1fr 1fr; gap:10px; margin-bottom:14px; }
  .del { border:2px solid var(--line); border-radius:14px; padding:10px; text-align:center; cursor:pointer; background:#fffdfb; transition:.2s; }
  .del.active { border-color:var(--brown); background:var(--pink-soft); }
  .del.disabled-opt { opacity:.45; cursor:not-allowed; pointer-events:none; background:#efe7e0; }
  .del .dt { font-size:12px; font-weight:700; }
  .del .dp { font-size:13px; font-weight:900; color:var(--brown-dark); margin-top:2px; }

  .summary { background:var(--pink-soft); border-radius:14px; padding:14px; margin:6px 0 16px; }
  .row { display:flex; justify-content:space-between; font-size:13px; padding:3px 0; }
  .row.total { font-size:18px; font-weight:900; border-top:1px solid var(--line); margin-top:5px; padding-top:7px; }
  .row.total span:last-child { color:var(--brown-dark); }
  .submit { width:100%; padding:15px; border:none; border-radius:14px; background:var(--brown); color:#fff; font-family:inherit; font-size:17px; font-weight:900; cursor:pointer; }
  .submit:disabled { opacity:.5; cursor:not-allowed; }
  .hint { font-size:12px; color:#b0503f; text-align:center; margin-top:8px; min-height:16px; }

  .faq { margin-top:20px; border-top:2px dashed var(--line); padding-top:14px; }
  .faq h4 { text-align:center; font-size:15px; font-weight:900; margin-bottom:10px; }
  .faq-item { background:var(--bg); border-radius:12px; padding:10px 14px; margin-bottom:8px; }
  .faq-item b { font-size:12px; display:block; }
  .faq-item span { font-size:12px; font-weight:600; color:var(--brown-dark); }

  .social { text-align:center; padding:10px 14px 36px; }
  .social h4 { font-size:15px; font-weight:900; color:var(--brown-dark); margin-bottom:14px; }
  .social-btns { display:flex; justify-content:center; gap:14px; flex-wrap:wrap; }
  .soc { display:flex; align-items:center; gap:8px; padding:11px 18px; border-radius:14px; background:var(--black); color:#fff; text-decoration:none; font-size:14px; font-weight:800; transition:.2s; }
  .soc svg { width:20px; height:20px; fill:currentColor; }
  .soc:hover { transform:translateY(-2px); background:var(--brown-dark); }
  .soc:focus-visible { outline:3px solid var(--brown); outline-offset:2px; }

  @media (prefers-reduced-motion: reduce) {
    .gift, .gift-lid, .spark, .intro-text { animation-duration:.01s; animation-delay:0s; }
  }
</style>
</head>
<body class="locked">

<!-- Gift intro -->
<div id="intro" onclick="closeIntro()">
  <div class="gift">
    <span class="spark">✨</span><span class="spark">🎀</span><span class="spark">✨</span><span class="spark">⭐</span><span class="spark">🌙</span>
    <div class="gift-lid"></div>
    <div class="gift-body"></div>
  </div>
  <div class="intro-text">مفاجأة لك من LUNA 🎁</div>
</div>

<div class="hero">
  <div class="moon">🌙</div>
  <h1>عروض LUNA الشتوية</h1>
  <p>شال + قفاز + عطر هدية — دفء وأناقة في باك واحد</p>
</div>

<div class="products" id="products"></div>

<div class="floating" id="floating">
  <div class="info">المنتجات: <b id="fc-count">0</b> — المجموع: <b id="fc-total">0 دج</b></div>
  <button onclick="scrollToOrder()">إتمام الطلب ←</button>
</div>

<div class="order-wrap" id="order-section">
  <div class="order">
    <h3>🛒 معلومات الطلب والتوصيل</h3>

    <div class="cart-box">
      <div class="t">🧾 العروض المختارة</div>
      <div id="cart-lines"><div class="empty">لم تختر أي عرض بعد</div></div>
    </div>

    <div class="fg"><label>الاسم واللقب</label><input type="text" id="fullname" placeholder="أدخل اسمك الكامل"></div>
    <div class="fg"><label>رقم الهاتف</label><input type="tel" id="phone" placeholder="06XXXXXXXX"></div>
    <div class="fg">
      <label>الولاية</label>
      <select id="wilaya" onchange="updateDelivery()"><option value="">— اختر الولاية —</option></select>
    </div>

    <label style="font-size:13px;font-weight:700;color:var(--muted);display:block;margin-bottom:6px;">نوع التوصيل</label>
    <div class="del-grid">
      <div class="del" id="btn-home" onclick="setDelivery('home')"><div class="dt">🏠 للمنزل</div><div class="dp" id="p-home">—</div></div>
      <div class="del" id="btn-office" onclick="setDelivery('office')"><div class="dt" id="t-office">🏢 للمكتب</div><div class="dp" id="p-office">—</div></div>
    </div>

    <div class="fg"><label>البلدية / العنوان</label><input type="text" id="address" placeholder="اسم البلدية أو العنوان"></div>

    <div class="summary">
      <div class="row"><span>مجموع المنتجات:</span><span id="sum-products">0 دج</span></div>
      <div class="row"><span>سعر التوصيل:</span><span id="sum-del">—</span></div>
      <div class="row total"><span>المجموع الكلي:</span><span id="sum-total">—</span></div>
    </div>

    <button class="submit" id="submit-btn" onclick="sendOrder()" disabled>تأكيد الطلب الآن</button>
    <div class="hint" id="hint"></div>

    <div class="faq">
      <h4>❓ أسئلة شائعة</h4>
      <div class="faq-item"><b>💳 طريقة الدفع؟</b><span>الدفع يد بيد عند استلام طلبيتك وإعادة معاينتها.</span></div>
      <div class="faq-item"><b>🚚 مدة التوصيل؟</b><span>التوصيل سريع من يومين إلى ثلاثة أيام كأقصى حد.</span></div>
    </div>
  </div>
</div>

<div class="social">
  <h4>تابعنا على مواقع التواصل 💗</h4>
  <div class="social-btns">
    <a class="soc" href="https://www.instagram.com/luna__pack?xtok=MzF1ZDh3cGk5bWt0" target="_blank" rel="noopener noreferrer">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M7.5 2h9A5.5 5.5 0 0 1 22 7.5v9a5.5 5.5 0 0 1-5.5 5.5h-9A5.5 5.5 0 0 1 2 16.5v-9A5.5 5.5 0 0 1 7.5 2zm0 2A3.5 3.5 0 0 0 4 7.5v9A3.5 3.5 0 0 0 7.5 20h9a3.5 3.5 0 0 0 3.5-3.5v-9A3.5 3.5 0 0 0 16.5 4h-9zM12 7a5 5 0 1 1 0 10 5 5 0 0 1 0-10zm0 2a3 3 0 1 0 0 6 3 3 0 0 0 0-6zm5.3-3.1a1.2 1.2 0 1 1 0 2.4 1.2 1.2 0 0 1 0-2.4z"/></svg>
      انستغرام
    </a>
    <a class="soc" href="https://www.facebook.com/share/1K33qXmHeA/" target="_blank" rel="noopener noreferrer">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M13.5 21v-8h2.7l.4-3.2h-3.1V7.9c0-.9.3-1.5 1.6-1.5h1.6V3.5c-.3 0-1.3-.1-2.4-.1-2.4 0-4 1.5-4 4.1v2.3H7.6V13h2.7v8h3.2z"/></svg>
      فيسبوك
    </a>
    <a class="soc" href="https://www.tiktok.com/@luna___pack?_r=1&amp;_t=ZS-9ApjTwB0iwS" target="_blank" rel="noopener noreferrer">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M16.6 3h-3.2v12.2a2.7 2.7 0 1 1-2.7-2.7c.3 0 .5 0 .8.1V9.3a5.9 5.9 0 1 0 5.1 5.9V8.6a7.4 7.4 0 0 0 4.3 1.4V6.8A4.3 4.3 0 0 1 16.6 3z"/></svg>
      تيك توك
    </a>
  </div>
</div>

<script>
var TELEGRAM_TOKEN = "8984328868:AAEjxhYfk_Iw6PhnSEIrsTZ3zCd_7zZHiLA";
var TELEGRAM_CHAT_ID = "8765345419";

var RATES = {
  "01 - Adrar": [1500, 750], "02 - Chlef": [900, 450], "03 - Laghouat": [1000, 500],
  "04 - Oum El Bouaghi": [750, 450], "05 - Batna": [450, 300], "06 - Bejaia": [800, 450],
  "07 - Biskra": [750, 450], "08 - Bechar": [1000, 500], "09 - Blida": [700, 450],
  "10 - Bouira": [900, 450], "11 - Tamanrasset": [1700, 800], "12 - Tebessa": [900, 450],
  "13 - Tlemcen": [950, 450], "14 - Tiaret": [950, 450], "15 - Tizi Ouzou": [700, 450],
  "16 - Alger": [700, 450], "17 - Djelfa": [1050, 600], "18 - Jijel": [800, 450],
  "19 - Setif": [700, 450], "20 - Saida": [900, 500], "21 - Skikda": [750, 450],
  "22 - Sidi Bel Abbes": [800, 0], "23 - Annaba": [750, 450], "24 - Guelma": [750, 450],
  "25 - Constantine": [700, 450], "26 - Medea": [800, 450], "27 - Mostaganem": [800, 450],
  "28 - Msila": [800, 450], "29 - Mascara": [800, 450], "30 - Ouargla": [900, 450],
  "31 - Oran": [800, 450], "32 - El Bayadh": [1150, 600], "33 - Illizi": [1700, 750],
  "34 - Bordj Bou Arreridj": [700, 450], "35 - Boumerdes": [700, 450], "36 - El Tarf": [750, 450],
  "37 - Tindouf": [1700, 0], "38 - Tissemsilt": [800, 450], "39 - El Oued": [900, 500],
  "40 - Khenchela": [600, 450], "41 - Souk Ahras": [700, 450], "42 - Tipaza": [850, 450],
  "43 - Mila": [700, 450], "44 - Ain Defla": [800, 450], "45 - Naama": [1050, 500],
  "46 - Ain Temouchent": [800, 450], "47 - Ghardaia": [950, 600], "48 - Relizane": [800, 500],
  "49 - Timimoun": [1400, 0], "50 - Bordj Badji Mokhtar": [1500, 0], "51 - Ouled Djellal": [950, 500],
  "52 - Beni Abbes": [1000, 0], "53 - In Salah": [1500, 750], "54 - In Guezzam": [1550, 0],
  "55 - Touggourt": [900, 500], "56 - Djanet": [1600, 750], "57 - El Mghair": [900, 500],
  "58 - El Meniaa": [1000, 0]
};

/* colors: خيارات الألوان تظهر فقط للعرض الذي يحتوي على هذا الحقل */
var PRODUCTS = [
  { id: 1, name: "عرض 2 شال + 2 قفاز + عطر هدية LUNA", price: 8500, img: "صورة1.png" },
  { id: 2, name: "عرض شال + قفاز + عطر هدية", price: 4600, img: "صورة2.png",
    colors: [
      { key: "shawl",  label: "🧣 الشال",   options: [ {n:"بني فاتح", c:"#c9a27e"}, {n:"أبيض", c:"#ffffff"} ] },
      { key: "gloves", label: "🧤 القفازات", options: [ {n:"أسود", c:"#1b1613"}, {n:"أبيض", c:"#ffffff"} ] }
    ] }
];

var cart = {};      // id -> qty
var picks = {};     // id -> {shawl:'..', gloves:'..'}
var currentDeliveryType = null;

function closeIntro() {
  var el = document.getElementById('intro');
  if (!el || el.classList.contains('hide')) return;
  el.classList.add('hide');
  document.body.classList.remove('locked');
  setTimeout(function(){ el.remove(); }, 800);
}
setTimeout(closeIntro, 3600);

function renderProducts() {
  var html = '';
  PRODUCTS.forEach(function(p) {
    var colorsHtml = '';
    if (p.colors) {
      colorsHtml = '<div class="colors" id="colors-' + p.id + '">';
      p.colors.forEach(function(g) {
        colorsHtml += '<div class="color-row"><div class="color-label">' + g.label + '</div><div class="swatches">';
        g.options.forEach(function(o) {
          colorsHtml += '<button type="button" class="swatch" data-p="' + p.id + '" data-g="' + g.key + '" data-n="' + o.n + '" onclick="pickColor(' + p.id + ',\'' + g.key + '\',\'' + o.n + '\')"><i style="background:' + o.c + '"></i>' + o.n + '</button>';
        });
        colorsHtml += '</div></div>';
      });
      colorsHtml += '</div>';
    }
    html += '<div class="card" id="card-' + p.id + '">' +
      '<div class="img-wrap"><img src="' + p.img + '" alt="' + p.name + '" onerror="this.parentElement.innerHTML=\'صورة العرض\'"></div>' +
      '<div class="p-name">' + p.name + '</div>' +
      '<div class="p-price">' + p.price + ' دج</div>' +
      '<div class="qty"><button onclick="changeQty(' + p.id + ',-1)" aria-label="إنقاص">−</button><span id="qty-' + p.id + '">0</span><button onclick="changeQty(' + p.id + ',1)" aria-label="زيادة">+</button></div>' +
      colorsHtml +
      '<button class="buy" onclick="buyNow(' + p.id + ')">⚡ اشتري الآن</button>' +
    '</div>';
  });
  document.getElementById('products').innerHTML = html;
}

function pickColor(id, group, name) {
  picks[id] = picks[id] || {};
  picks[id][group] = name;
  document.querySelectorAll('.swatch[data-p="' + id + '"][data-g="' + group + '"]').forEach(function(b) {
    b.classList.toggle('active', b.getAttribute('data-n') === name);
  });
  updateCartUI();
}

function setQty(id, n) {
  cart[id] = n;
  document.getElementById('qty-' + id).innerText = n;
  document.getElementById('card-' + id).classList.toggle('in-cart', n > 0);
  updateCartUI();
}
function changeQty(id, d) { setQty(id, Math.max(0, (cart[id] || 0) + d)); }

function buyNow(id) {
  if (!cart[id]) setQty(id, 1);
  var p = PRODUCTS.filter(function(x){ return x.id === id; })[0];
  if (p.colors && !colorsComplete(p)) {
    document.getElementById('colors-' + id).scrollIntoView({ behavior: 'smooth', block: 'center' });
    return;
  }
  scrollToOrder();
}

function colorsComplete(p) {
  if (!p.colors) return true;
  var s = picks[p.id] || {};
  return p.colors.every(function(g) { return !!s[g.key]; });
}

function colorText(p) {
  if (!p.colors) return '';
  var s = picks[p.id] || {};
  return p.colors.map(function(g) { return g.label.replace(/^\S+\s/, '') + ': ' + (s[g.key] || '—'); }).join(' | ');
}

function getCartItems() {
  var items = [];
  PRODUCTS.forEach(function(p) {
    var q = cart[p.id] || 0;
    if (q > 0) items.push({ p: p, qty: q, lineTotal: q * p.price, colors: colorText(p) });
  });
  return items;
}
function getSubtotal() { return getCartItems().reduce(function(s, i) { return s + i.lineTotal; }, 0); }
function allColorsChosen() { return getCartItems().every(function(i) { return colorsComplete(i.p); }); }

function updateCartUI() {
  var items = getCartItems();
  var count = items.reduce(function(s, i) { return s + i.qty; }, 0);
  var sub = getSubtotal();
  document.getElementById('fc-count').innerText = count;
  document.getElementById('fc-total').innerText = sub + ' دج';
  document.getElementById('floating').classList.toggle('visible', count > 0);

  var html = '';
  if (!items.length) html = '<div class="empty">لم تختر أي عرض بعد</div>';
  items.forEach(function(i) {
    html += '<div class="line"><span>' + i.p.name + ' × ' + i.qty + (i.colors ? '<small>' + i.colors + '</small>' : '') + '</span><span>' + i.lineTotal + ' دج</span></div>';
  });
  document.getElementById('cart-lines').innerHTML = html;
  document.getElementById('sum-products').innerText = sub + ' دج';
  calculateTotal();
}

function scrollToOrder() { document.getElementById('order-section').scrollIntoView({ behavior: 'smooth', block: 'start' }); }

document.addEventListener('DOMContentLoaded', function() {
  renderProducts();
  var sel = document.getElementById('wilaya');
  for (var w in RATES) {
    var o = document.createElement('option');
    o.value = w; o.textContent = w;
    sel.appendChild(o);
  }
});

function updateDelivery() {
  var w = document.getElementById('wilaya').value;
  var btnOffice = document.getElementById('btn-office');
  if (!w || !RATES[w]) return;
  var home = RATES[w][0], office = RATES[w][1];
  document.getElementById('p-home').innerText = home ? home + ' دج' : 'غير متوفر';
  if (office === 0) {
    btnOffice.classList.add('disabled-opt');
    btnOffice.classList.remove('active');
    document.getElementById('t-office').innerText = '🏢 لا يوجد مكتب في ولايتك';
    document.getElementById('p-office').innerText = 'غير متوفر';
    if (currentDeliveryType === 'office') {
      currentDeliveryType = 'home';
      document.getElementById('btn-home').classList.add('active');
    }
  } else {
    btnOffice.classList.remove('disabled-opt');
    document.getElementById('t-office').innerText = '🏢 للمكتب';
    document.getElementById('p-office').innerText = office + ' دج';
  }
  calculateTotal();
}

function setDelivery(type) {
  var w = document.getElementById('wilaya').value;
  if (!w || !RATES[w]) return;
  if (type === 'office' && RATES[w][1] === 0) return;
  currentDeliveryType = type;
  document.getElementById('btn-home').classList.toggle('active', type === 'home');
  document.getElementById('btn-office').classList.toggle('active', type === 'office');
  calculateTotal();
}

function calculateTotal() {
  var w = document.getElementById('wilaya').value;
  var sub = getSubtotal();
  var hint = document.getElementById('hint');
  var btn = document.getElementById('submit-btn');
  hint.innerText = '';

  if (sub === 0 || !w || !currentDeliveryType || !RATES[w]) {
    document.getElementById('sum-del').innerText = '—';
    document.getElementById('sum-total').innerText = '—';
    btn.disabled = true;
    return;
  }
  var cost = currentDeliveryType === 'home' ? RATES[w][0] : RATES[w][1];
  document.getElementById('sum-del').innerText = cost + ' دج';
  document.getElementById('sum-total').innerText = (sub + cost) + ' دج';

  if (!allColorsChosen()) {
    hint.innerText = 'يرجى اختيار ألوان الشال والقفازات أعلاه.';
    btn.disabled = true;
    return;
  }
  btn.disabled = false;
}

function sendOrder() {
  var name = document.getElementById('fullname').value.trim();
  var phone = document.getElementById('phone').value.trim();
  var wilaya = document.getElementById('wilaya').value;
  var address = document.getElementById('address').value.trim();
  var items = getCartItems();
  var sub = getSubtotal();

  if (!name || !phone) { alert('يرجى كتابة الاسم ورقم الهاتف'); return; }
  if (!items.length) { alert('يرجى اختيار عرض واحد على الأقل'); return; }
  if (!allColorsChosen()) { alert('يرجى اختيار الألوان'); return; }

  var deliveryText = currentDeliveryType === 'home' ? 'توصيل للمنزل' : 'توصيل للمكتب';
  var cost = currentDeliveryType === 'home' ? RATES[wilaya][0] : RATES[wilaya][1];
  var total = sub + cost;

  var btn = document.getElementById('submit-btn');
  btn.disabled = true;
  btn.innerText = 'جاري إرسال الطلب...';

  var itemsText = items.map(function(i) {
    return '• ' + i.p.name + ' × ' + i.qty + ' = ' + i.lineTotal + ' دج' + (i.colors ? '\n   🎨 ' + i.colors : '');
  }).join('\n');

  var message = '🛒 طلبية جديدة\n\n' +
    '👤 الاسم: ' + name + '\n' +
    '📞 الهاتف: ' + phone + '\n' +
    '📍 الولاية: ' + wilaya + '\n' +
    '🏠 العنوان/البلدية: ' + (address || 'غير محدد') + '\n\n' +
    '📦 المنتجات:\n' + itemsText + '\n\n' +
    '🚚 نوع التوصيل: ' + deliveryText + ' (' + cost + ' دج)\n' +
    '💰 مجموع المنتجات: ' + sub + ' دج\n' +
    '💰 المجموع الكلي: ' + total + ' دج';

  fetch('https://api.telegram.org/bot' + TELEGRAM_TOKEN + '/sendMessage', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ chat_id: TELEGRAM_CHAT_ID, text: message })
  })
  .then(function(r) { return r.json(); })
  .then(function(d) {
    if (d.ok) {
      alert('تم تسجيل طلبك بنجاح! وسنتصل بك قريباً لتأكيده.');
      location.reload();
    } else {
      alert('حدث خطأ أثناء إرسال الطلب، يرجى المحاولة لاحقاً.');
      btn.disabled = false; btn.innerText = 'تأكيد الطلب الآن';
    }
  })
  .catch(function() {
    alert('تعذر الاتصال بالخادم، تحقق من الاتصال بالإنترنت.');
    btn.disabled = false; btn.innerText = 'تأكيد الطلب الآن';
  });
}
</script>
</body>
</html>
