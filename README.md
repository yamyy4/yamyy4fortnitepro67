<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Чай-хаус — восточная кухня, кофе и выпечка</title>
<style>
  :root{
    --brown-dark:#2b1810;
    --brown:#5c3a21;
    --brown-mid:#7a4a28;
    --yellow:#ffc107;
    --yellow-deep:#f0a500;
    --cream:#fff8e7;
    --milk:#fffdf7;
    --text-dark:#2b1810;
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    font-family:'Segoe UI', Tahoma, sans-serif;
    background:var(--cream);
    color:var(--text-dark);
    line-height:1.6;
    overflow-x:hidden;
  }

  /* ===== ШАПКА ===== */
  header{
    position:fixed;top:0;left:0;right:0;
    background:var(--brown-dark);
    backdrop-filter:blur(8px);
    z-index:100;
    padding:14px 6%;
    display:flex;justify-content:space-between;align-items:center;
    box-shadow:0 2px 20px rgba(0,0,0,.3);
    border-bottom:3px solid var(--yellow);
    transition:padding .3s ease;
  }
  .logo{
    font-size:1.4rem;font-weight:800;color:var(--cream);
    letter-spacing:.5px;cursor:pointer;
    transition:transform .35s ease, letter-spacing .35s ease;
  }
  .logo:hover{
    transform:scale(1.06);
    letter-spacing:1.5px;
  }
  .logo span{color:var(--yellow);}
  nav a{
    color:var(--cream);text-decoration:none;margin-left:26px;
    font-size:.95rem;font-weight:600;transition:.3s;position:relative;
    padding:6px 4px;
    display:inline-block;
  }
  nav a:hover{
    color:var(--yellow);
    transform:translateY(-2px);
  }
  nav a::after{
    content:'';position:absolute;left:0;bottom:0;width:0;height:2px;
    background:var(--yellow);transition:width .35s ease;
    box-shadow:0 0 8px var(--yellow);
  }
  nav a:hover::after{width:100%;}

  /* ===== ДЕКОРАТИВНЫЙ РАЗДЕЛИТЕЛЬ МЕЖДУ СЕКЦИЯМИ ===== */
  .divider{
    display:flex;justify-content:center;align-items:center;
    gap:14px;
    padding:20px 0;
    background:inherit;
  }
  .divider .line{
    width:60px;height:2px;
    background:linear-gradient(90deg,transparent,var(--yellow),transparent);
    transition:width .4s ease;
  }
  .divider .diamond{
    color:var(--yellow);font-size:1.3rem;
    animation:spin 6s linear infinite;
    display:inline-block;
  }
  .divider:hover .line{width:120px;}
  @keyframes spin{
    from{transform:rotate(0deg);}
    to{transform:rotate(360deg);}
  }

  /* ===== ГЕРОЙ ===== */
  .hero{
    min-height:100vh;
    display:flex;align-items:center;justify-content:center;
    text-align:center;
    padding:140px 6% 100px;
    background:
      radial-gradient(circle at 80% 20%, rgba(255,193,7,.18), transparent 45%),
      linear-gradient(135deg,var(--brown-dark) 0%,var(--brown) 55%,var(--brown-mid) 100%);
    color:var(--cream);
    position:relative;
    overflow:hidden;
  }
  .hero::before{
    content:'';position:absolute;width:600px;height:600px;
    background:radial-gradient(circle, rgba(255,193,7,.35), transparent 65%);
    top:-200px;right:-200px;border-radius:50%;
    animation:float 12s ease-in-out infinite;
  }
  .hero::after{
    content:'';position:absolute;width:420px;height:420px;
    background:radial-gradient(circle, rgba(255,193,7,.15), transparent 70%);
    bottom:-160px;left:-120px;border-radius:50%;
    animation:float 15s ease-in-out infinite reverse;
  }
  @keyframes float{
    0%,100%{transform:translate(0,0);}
    50%{transform:translate(-30px,30px);}
  }
  .hero-content{position:relative;z-index:2;max-width:820px;}
  .hero .badge{
    display:inline-block;
    background:var(--yellow);
    color:var(--brown-dark);
    padding:9px 22px;border-radius:30px;
    font-size:.85rem;font-weight:800;letter-spacing:1.5px;
    margin-bottom:26px;
    animation:fadeUp .8s ease, badgePulse 3s ease-in-out infinite;
    box-shadow:0 6px 20px rgba(255,193,7,.4);
    transition:transform .3s ease;
    cursor:default;
  }
  .hero .badge:hover{transform:scale(1.08) rotate(-2deg);}
  @keyframes badgePulse{
    0%,100%{box-shadow:0 6px 20px rgba(255,193,7,.4);}
    50%{box-shadow:0 6px 30px rgba(255,193,7,.8);}
  }
  .hero h1{
    font-size:clamp(2.2rem,5.5vw,4.3rem);
    line-height:1.12;margin-bottom:24px;
    animation:fadeUp 1s ease .1s both;
    font-weight:800;
  }
  .hero h1 em{color:var(--yellow);font-style:normal;}
  .hero p{
    font-size:clamp(1rem,2vw,1.25rem);
    max-width:640px;margin:0 auto 40px;
    opacity:.95;
    animation:fadeUp 1s ease .2s both;
  }
  .btn{
    display:inline-block;
    background:var(--yellow);color:var(--brown-dark);
    padding:16px 42px;border-radius:50px;
    text-decoration:none;font-weight:800;font-size:1rem;
    transition:.35s;
    box-shadow:0 8px 25px rgba(255,193,7,.45);
    animation:fadeUp 1s ease .3s both;
    position:relative;
    overflow:hidden;
  }
  .btn::before{
    content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;
    background:linear-gradient(90deg,transparent,rgba(255,255,255,.5),transparent);
    transition:left .5s ease;
  }
  .btn:hover::before{left:100%;}
  .btn:hover{
    transform:translateY(-4px) scale(1.05);
    box-shadow:0 14px 40px rgba(255,193,7,.75);
    background:var(--yellow-deep);
  }
  @keyframes fadeUp{
    from{opacity:0;transform:translateY(30px);}
    to{opacity:1;transform:translateY(0);}
  }

  /* ===== ОБЩИЕ СТИЛИ СЕКЦИЙ ===== */
  .section-title{
    text-align:center;
    font-size:clamp(1.8rem,4vw,2.8rem);
    margin-bottom:16px;
    color:var(--brown-dark);
    font-weight:800;
    transition:letter-spacing .4s ease, color .3s ease;
    cursor:default;
  }
  .section-title:hover{
    letter-spacing:2px;
    color:var(--brown-mid);
  }
  .section-title::after{
    content:'';display:block;
    width:70px;height:4px;margin:14px auto 0;
    background:var(--yellow);border-radius:4px;
    transition:width .4s ease;
  }
  .section-title:hover::after{width:130px;}
  .section-sub{
    text-align:center;
    color:var(--brown);
    max-width:640px;
    margin:0 auto 55px;
    font-size:1.05rem;
  }

  /* ===== ВОСТОЧНАЯ КУХНЯ ===== */
  .eastern{
    padding:100px 6% 60px;
    background:var(--milk);
    position:relative;
    overflow:hidden;
  }
  .eastern::before{
    content:'☪';
    position:absolute;top:40px;right:8%;
    font-size:9rem;color:rgba(255,193,7,.12);
    font-weight:bold;
    animation:float 10s ease-in-out infinite;
  }
  .eastern-text{
    max-width:880px;
    margin:0 auto;
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:40px;
    align-items:center;
    position:relative;z-index:2;
  }
  .eastern-text p{
    color:var(--brown);
    font-size:1.06rem;
    margin-bottom:16px;
    transition:.3s;
  }
  .eastern-text p:hover{
    transform:translateX(6px);
    color:var(--brown-dark);
  }
  .eastern-text .accent{color:var(--brown-dark);font-weight:700;}
  .eastern-visual{
    display:flex;flex-wrap:wrap;gap:16px;justify-content:center;
  }
  .eastern-visual .chip{
    background:var(--yellow);
    color:var(--brown-dark);
    padding:14px 20px;border-radius:14px;
    font-weight:700;
    font-size:.95rem;
    box-shadow:0 6px 18px rgba(255,193,7,.35);
    transition:.35s cubic-bezier(.2,.8,.3,1.4);
    cursor:default;
  }
  .eastern-visual .chip:hover{
    transform:translateY(-6px) rotate(-3deg) scale(1.08);
    box-shadow:0 14px 30px rgba(255,193,7,.65);
    background:var(--yellow-deep);
  }

  /* ===== МЕНЮ ===== */
  .menu{
    padding:80px 6% 100px;
    background:linear-gradient(180deg,var(--cream),var(--milk));
    position:relative;
  }
  .menu-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
    gap:26px;
    max-width:1100px;
    margin:0 auto;
  }
  .menu-item{
    background:#fff;
    border-radius:18px;
    padding:30px;
    display:flex;align-items:center;gap:22px;
    box-shadow:0 6px 24px rgba(43,24,16,.09);
    transition:.4s cubic-bezier(.2,.8,.3,1.2);
    border-left:6px solid var(--yellow);
    position:relative;
    overflow:hidden;
    cursor:default;
  }
  .menu-item::before{
    content:'';position:absolute;inset:0;
    background:linear-gradient(135deg,rgba(255,193,7,.08),transparent 60%);
    opacity:0;transition:opacity .4s ease;
    pointer-events:none;
  }
  .menu-item:hover::before{opacity:1;}
  .menu-item:hover{
    transform:translateX(10px) translateY(-4px);
    box-shadow:0 18px 40px rgba(43,24,16,.22);
    border-left-color:var(--yellow-deep);
  }
  .menu-item .emoji{
    font-size:3rem;flex-shrink:0;
    transition:.45s cubic-bezier(.2,.8,.3,1.5);
    display:inline-block;
  }
  .menu-item:hover .emoji{
    transform:scale(1.25) rotate(-12deg);
  }
  .menu-item h4{
    font-size:1.22rem;margin-bottom:6px;color:var(--brown-dark);font-weight:700;
    transition:.3s;
  }
  .menu-item:hover h4{color:var(--brown-mid);}
  .menu-item .desc{color:var(--brown);font-size:.92rem;}
  .menu-item .price{
    margin-left:auto;
    font-weight:800;
    color:var(--brown-dark);
    font-size:1.2rem;
    white-space:nowrap;
    background:var(--yellow);
    padding:6px 14px;
    border-radius:10px;
    transition:.35s cubic-bezier(.2,.8,.3,1.4);
  }
  .menu-item:hover .price{
    transform:scale(1.12);
    background:var(--yellow-deep);
    box-shadow:0 6px 16px rgba(255,193,7,.55);
  }

  /* ===== ОТЗЫВЫ ===== */
  .reviews{
    padding:80px 6% 100px;
    background:var(--brown-dark);
    color:var(--cream);
    position:relative;
    overflow:hidden;
  }
  .reviews::before{
    content:'❝';
    position:absolute;top:30px;left:6%;
    font-size:12rem;color:rgba(255,193,7,.08);
    line-height:1;
    pointer-events:none;
  }
  .reviews .section-title{color:var(--cream);}
  .reviews .section-title:hover{color:var(--yellow);}
  .reviews .section-sub{color:#d8c9b3;}
  .review-list{
    max-width:820px;
    margin:0 auto 50px;
    display:flex;flex-direction:column;gap:18px;
    position:relative;z-index:2;
  }
  .review-card{
    background:rgba(255,255,255,.06);
    border-left:5px solid var(--yellow);
    border-radius:14px;
    padding:22px 26px;
    animation:fadeUp .5s ease;
    transition:.4s cubic-bezier(.2,.8,.3,1.2);
    cursor:default;
  }
  .review-card:hover{
    transform:translateX(8px) scale(1.02);
    background:rgba(255,193,7,.1);
    border-left-color:var(--yellow-deep);
    box-shadow:0 12px 30px rgba(0,0,0,.3), 0 0 20px rgba(255,193,7,.2);
  }
  .review-card .head{
    display:flex;justify-content:space-between;align-items:center;
    margin-bottom:8px;
  }
  .review-card .name{
    color:var(--yellow);font-weight:700;font-size:1.05rem;
    transition:.3s;
  }
  .review-card:hover .name{color:var(--yellow-deep);letter-spacing:.5px;}
  .review-card .date{
    color:#a89880;font-size:.82rem;
  }
  .review-card .text{color:#efe6d6;font-size:.98rem;}

  /* Форма отзыва */
  .review-form-wrap{
    max-width:820px;
    margin:0 auto;
    background:rgba(255,255,255,.05);
    border:2px dashed var(--yellow);
    border-radius:20px;
    padding:34px 30px;
    position:relative;z-index:2;
    transition:.4s ease;
  }
  .review-form-wrap:hover{
    border-color:var(--yellow-deep);
    background:rgba(255,193,7,.06);
    box-shadow:0 0 30px rgba(255,193,7,.15);
  }
  .review-form-wrap h3{
    color:var(--yellow);
    font-size:1.35rem;
    margin-bottom:6px;
    font-weight:800;
    transition:.3s;
  }
  .review-form-wrap:hover h3{letter-spacing:1px;}
  .review-form-wrap .hint{
    color:#c9b89c;font-size:.9rem;margin-bottom:22px;
  }
  .review-form-wrap input,
  .review-form-wrap textarea{
    width:100%;
    background:rgba(255,255,255,.95);
    border:2px solid transparent;
    border-radius:12px;
    padding:13px 16px;
    font-family:inherit;font-size:.98rem;
    color:var(--brown-dark);
    margin-bottom:14px;
    transition:.25s;
    outline:none;
    resize:vertical;
  }
  .review-form-wrap input:focus,
  .review-form-wrap textarea:focus{
    border-color:var(--yellow);
    box-shadow:0 0 0 4px rgba(255,193,7,.25);
    transform:translateY(-2px);
  }
  .review-form-wrap textarea{min-height:100px;}
  .review-form-wrap button{
    background:var(--yellow);
    color:var(--brown-dark);
    border:none;
    padding:14px 38px;
    border-radius:50px;
    font-weight:800;font-size:1rem;
    cursor:pointer;
    transition:.35s cubic-bezier(.2,.8,.3,1.4);
    box-shadow:0 8px 22px rgba(255,193,7,.4);
    font-family:inherit;
  }
  .review-form-wrap button:hover{
    background:var(--yellow-deep);
    transform:translateY(-3px) scale(1.05);
    box-shadow:0 14px 34px rgba(255,193,7,.65);
  }
  .review-form-wrap button:active{
    transform:translateY(0) scale(.98);
  }

  /* ===== КОНТАКТЫ ===== */
  .contact{
    padding:80px 6% 100px;
    background:var(--milk);
    text-align:center;
  }
  .contact-info{
    display:flex;flex-wrap:wrap;justify-content:center;gap:32px;
    margin-top:48px;
  }
  .contact-info div{
    background:#fff;
    padding:34px 46px;
    border-radius:16px;
    min-width:260px;
    transition:.45s cubic-bezier(.2,.8,.3,1.3);
    border-top:5px solid var(--yellow);
    box-shadow:0 6px 22px rgba(43,24,16,.08);
    cursor:default;
    position:relative;
    overflow:hidden;
  }
  .contact-info div::after{
    content:'';position:absolute;
    top:0;left:0;right:0;height:5px;
    background:var(--yellow-deep);
    transform:scaleX(0);transform-origin:left;
    transition:transform .45s ease;
  }
  .contact-info div:hover::after{transform:scaleX(1);}
  .contact-info div:hover{
    transform:translateY(-10px) scale(1.03);
    box-shadow:0 20px 40px rgba(43,24,16,.2);
    border-top-color:var(--yellow-deep);
  }
  .contact-info .ic{
    font-size:2.2rem;display:block;margin-bottom:12px;
    transition:.4s cubic-bezier(.2,.8,.3,1.5);
  }
  .contact-info div:hover .ic{
    transform:scale(1.3) rotate(-8deg);
    filter:drop-shadow(0 0 10px rgba(255,193,7,.6));
  }
  .contact-info h4{
    color:var(--brown-dark);margin-bottom:8px;font-size:1.15rem;
    transition:.3s;
  }
  .contact-info div:hover h4{letter-spacing:.5px;}
  .contact-info p{color:var(--brown);font-size:1rem;font-weight:600;}

  /* ===== ПОДВАЛ ===== */
  footer{
    background:var(--brown-dark);
    color:var(--cream);
    text-align:center;
    padding:36px 6%;
    font-size:.9rem;
    border-top:3px solid var(--yellow);
    transition:.3s;
  }
  footer:hover{
    letter-spacing:.5px;
    border-top-color:var(--yellow-deep);
  }
  footer span{color:var(--yellow);font-weight:700;}

  /* ===== КНОПКА ВВЕРХ ===== */
  .to-top{
    position:fixed;bottom:26px;right:26px;
    width:52px;height:52px;
    background:var(--yellow);color:var(--brown-dark);
    border:none;border-radius:50%;
    font-size:1.4rem;font-weight:800;
    cursor:pointer;
    box-shadow:0 8px 22px rgba(255,193,7,.5);
    opacity:0;visibility:hidden;
    transform:translateY(20px);
    transition:.4s cubic-bezier(.2,.8,.3,1.4);
    z-index:99;
  }
  .to-top.show{opacity:1;visibility:visible;transform:translateY(0);}
  .to-top:hover{
    background:var(--yellow-deep);
    transform:translateY(-5px) scale(1.1);
    box-shadow:0 14px 32px rgba(255,193,7,.7);
  }

  /* ===== АДАПТИВ ===== */
  @media(max-width:820px){
    .eastern-text{grid-template-columns:1fr;}
  }
  @media(max-width:768px){
    nav a{margin-left:14px;font-size:.82rem;}
    .logo{font-size:1.1rem;}
    .menu-item{flex-direction:column;text-align:center;}
    .menu-item .price{margin-left:0;}
    .menu-item:hover{transform:translateY(-6px) scale(1.02);}
    .review-card:hover{transform:translateX(0) scale(1.02);}
  }
  @media(max-width:560px){
    nav{display:none;}
  }
</style>
</head>
<body>

<!-- ШАПКА -->
<header>
  <div class="logo">☕ Чай-<span>хаус</span></div>
  <nav>
    <a href="#eastern">Кухня</a>
    <a href="#menu">Меню</a>
    <a href="#reviews">Отзывы</a>
    <a href="#contact">Контакты</a>
  </nav>
</header>

<!-- ГЕРОЙ -->
<section class="hero">
  <div class="hero-content">
    <div class="badge">✦ ВОСТОЧНЫЙ ВКУС И АРОМАТ ✦</div>
    <h1>Чай-хаус —<br>там, где <em>вкусно</em> по-восточному</h1>
    <p>Плов, мраморное мясо, бифштекс и домашние пельмени. Ароматный кофе, густые милкшейки и свежие булочки. Мы собрали лучшее из восточной кухни и уюта кофейни.</p>
    <a href="#menu" class="btn">Смотреть меню →</a>
  </div>
</section>

<!-- ВОСТОЧНАЯ КУХНЯ -->
<section class="eastern" id="eastern">
  <h2 class="section-title">Восточная кухня</h2>
  <p class="section-sub">Честные порции, настоящие специи и рецепты, которые передают из поколения в поколение</p>

  <div class="eastern-text">
    <div>
      <p><span class="accent">Восточная кухня</span> — это щедрость, аромат и глубина вкуса. У нас готовят так, как готовят дома: не торопясь, на живом огне и с уважением к каждому ингредиенту.</p>
      <p>Рассыпчатый <span class="accent">плов</span> с мраморным мясом, сочный <span class="accent">бифштекс</span> на гриле, домашние <span class="accent">пельмени</span> ручной лепки — и всё это под чашку хорошего кофе или густой милкшейк.</p>
      <p>А на десерт — свежие <span class="accent">булочки</span> из печи: с корицей, с маком, с шоколадом. Заходите — у нас пахнет домом.</p>
    </div>
    <div class="eastern-visual">
      <div class="chip">🍲 Плов</div>
      <div class="chip">🥩 Мраморное мясо</div>
      <div class="chip">🥟 Пельмени</div>
      <div class="chip">🥩 Бифштекс</div>
      <div class="chip">🥐 Булочки</div>
      <div class="chip">☕ Кофе</div>
      <div class="chip">🥤 Милкшейки</div>
    </div>
  </div>
</section>

<!-- РАЗДЕЛИТЕЛЬ -->
<div class="divider" style="background:var(--milk);">
  <span class="line"></span>
  <span class="diamond">✦</span>
  <span class="line"></span>
</div>

<!-- МЕНЮ -->
<section class="menu" id="menu">
  <h2 class="section-title">Наше меню</h2>
  <p class="section-sub">Цены указаны приблизительно — уточняйте в зале</p>
  <div class="menu-grid">
    <div class="menu-item">
      <span class="emoji">☕</span>
      <div>
        <h4>Кофе</h4>
        <div class="desc">Американо, капучино, латте на мягком молоке</div>
      </div>
      <span class="price">~180 ₽</span>
    </div>
    <div class="menu-item">
      <span class="emoji">🥟</span>
      <div>
        <h4>Пельмени</h4>
        <div class="desc">Домашние, ручной лепки, с бульоном</div>
      </div>
      <span class="price">~350 ₽</span>
    </div>
    <div class="menu-item">
      <span class="emoji">🥤</span>
      <div>
        <h4>Милкшейки</h4>
        <div class="desc">Густые, на 100% молоке, ваниль / шоколад</div>
      </div>
      <span class="price">~250 ₽</span>
    </div>
    <div class="menu-item">
      <span class="emoji">🥩</span>
      <div>
        <h4>Бифштекс</h4>
        <div class="desc">Сочный, с пряными специями, на гриле</div>
      </div>
      <span class="price">~450 ₽</span>
    </div>
    <div class="menu-item">
      <span class="emoji">🍲</span>
      <div>
        <h4>Плов</h4>
        <div class="desc">Рассыпчатый, с бараниной и зирой</div>
      </div>
      <span class="price">~380 ₽</span>
    </div>
    <div class="menu-item">
      <span class="emoji">🥩</span>
      <div>
        <h4>Мраморное мясо</h4>
        <div class="desc">Нежная текстура, обжарка на живом огне</div>
      </div>
      <span class="price">~550 ₽</span>
    </div>
    <div class="menu-item">
      <span class="emoji">🥐</span>
      <div>
        <h4>Разные булочки</h4>
        <div class="desc">С корицей, маком, шоколадом — из печи</div>
      </div>
      <span class="price">~130 ₽</span>
    </div>
  </div>
</section>

<!-- РАЗДЕЛИТЕЛЬ -->
<div class="divider" style="background:var(--milk);">
  <span class="line"></span>
  <span class="diamond">✦</span>
  <span class="line"></span>
</div>

<!-- ОТЗЫВЫ + ФОРМА -->
<section class="reviews" id="reviews">
  <h2 class="section-title">Отзывы гостей</h2>
  <p class="section-sub">Пишите отзывы прямо здесь — мы читаем каждый</p>

  <div class="review-list" id="reviewList">
    <div class="review-card">
      <div class="head">
        <span class="name">Анна</span>
        <span class="date">недавно</span>
      </div>
      <div class="text">Плов просто невероятный — как у бабушки в Ташкенте! И кофе отличный. Теперь хожу каждую неделю.</div>
    </div>
    <div class="review-card">
      <div class="head">
        <span class="name">Дмитрий</span>
        <span class="date">недавно</span>
      </div>
      <div class="text">Мраморное мясо — огонь. Порции большие, цены адекватные. Пельмени ручной лепки отдельный респект.</div>
    </div>
    <div class="review-card">
      <div class="head">
        <span class="name">Марина</span>
        <span class="date">недавно</span>
      </div>
      <div class="text">Булочки свежайшие, милкшейк густой и вкусный. Атмосфера уютная, персонал приветливый. Рекомендую!</div>
    </div>
  </div>

  <div class="review-form-wrap">
    <h3>✍️ Оставить отзыв</h3>
    <p class="hint">Отзыв сохранится прямо на этой странице.</p>
    <input type="text" id="reviewName" placeholder="Ваше имя" maxlength="40">
    <textarea id="reviewText" placeholder="Ваш отзыв..." maxlength="500"></textarea>
    <button onclick="addReview()">Отправить отзыв</button>
  </div>
</section>

<!-- РАЗДЕЛИТЕЛЬ -->
<div class="divider" style="background:var(--brown-dark);">
  <span class="line"></span>
  <span class="diamond">✦</span>
  <span class="line"></span>
</div>

<!-- КОНТАКТЫ (один адрес + телефон) -->
<section class="contact" id="contact">
  <h2 class="section-title">Заходите в гости</h2>
  <p class="section-sub">Ждём вас каждый день</p>
  <div class="contact-info">
    <div>
      <span class="ic">📍</span>
      <h4>Адрес</h4>
      <p>Ясеневая улица, 19к1</p>
    </div>
    <div>
      <span class="ic">📞</span>
      <h4>Телефон</h4>
      <p>+7 936 192 11 11</p>
    </div>
  </div>
</section>

<!-- ПОДВАЛ -->
<footer>
  © 2025 <span>Чай-хаус</span>. Восточный вкус и уют ☕
</footer>

<!-- КНОПКА ВВЕРХ -->
<button class="to-top" id="toTop" aria-label="Наверх">↑</button>

<script>
  // Плавное появление карточек при скролле
  const observer = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
        observer.unobserve(e.target);
      }
    });
  },{threshold:.15});

  document.querySelectorAll('.menu-item, .review-card').forEach(el=>{
    el.style.opacity = '0';
    el.style.transform = 'translateY(30px)';
    el.style.transition = 'opacity .7s ease, transform .7s ease';
    observer.observe(el);
  });

  // === ОТЗЫВЫ (localStorage) ===
  const STORAGE_KEY = 'chaihouse_reviews_v1';

  function escapeHtml(str){
    return str.replace(/[&<>"']/g, s => ({
      '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'
    }[s]));
  }

  function renderSavedReviews(){
    let saved = [];
    try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]'); }
    catch(e){ saved = []; }

    const list = document.getElementById('reviewList');
    saved.forEach(r=>{
      const div = document.createElement('div');
      div.className = 'review-card';
      div.innerHTML = `
        <div class="head">
          <span class="name">${escapeHtml(r.name)}</span>
          <span class="date">${escapeHtml(r.date)}</span>
        </div>
        <div class="text">${escapeHtml(r.text)}</div>
      `;
      list.appendChild(div);
    });
  }

  function addReview(){
    const nameEl = document.getElementById('reviewName');
    const textEl = document.getElementById('reviewText');
    const name = nameEl.value.trim();
    const text = textEl.value.trim();

    if(!name){
      alert('Пожалуйста, напишите ваше имя 🙂');
      nameEl.focus();
      return;
    }
    if(text.length < 5){
      alert('Отзыв слишком короткий — напишите чуть подробнее 🙂');
      textEl.focus();
      return;
    }

    const now = new Date();
    const dateStr = now.toLocaleDateString('ru-RU', {day:'numeric', month:'long', year:'numeric'});

    let saved = [];
    try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]'); }
    catch(e){ saved = []; }
    saved.unshift({ name, text, date: dateStr });
    try { localStorage.setItem(STORAGE_KEY, JSON.stringify(saved)); }
    catch(e){}

    const list = document.getElementById('reviewList');
    const div = document.createElement('div');
    div.className = 'review-card';
    div.innerHTML = `
      <div class="head">
        <span class="name">${escapeHtml(name)}</span>
        <span class="date">${escapeHtml(dateStr)}</span>
      </div>
      <div class="text">${escapeHtml(text)}</div>
    `;
    list.insertBefore(div, list.firstChild);

    nameEl.value = '';
    textEl.value = '';

    div.scrollIntoView({behavior:'smooth', block:'center'});
  }

  // === Кнопка вверх ===
  const toTop = document.getElementById('toTop');
  window.addEventListener('scroll', ()=>{
    if(window.scrollY > 400) toTop.classList.add('show');
    else toTop.classList.remove('show');
  });
  toTop.addEventListener('click', ()=>{
    window.scrollTo({top:0, behavior:'smooth'});
  });

  document.addEventListener('DOMContentLoaded', renderSavedReviews);
</script>

</body>
</html>
