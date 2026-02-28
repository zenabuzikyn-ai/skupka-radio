<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Скупка радіодеталей Україна</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Arial, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: white;
        }

        /* Шапка */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 30px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }

        .site-title h1 {
            font-size: 28px;
            font-weight: 600;
        }

        .site-title span {
            font-size: 18px;
            opacity: 0.9;
            display: block;
        }

        /* Меню-бургер */
        .menu-btn {
            cursor: pointer;
            z-index: 100;
        }

        .menu-btn span {
            display: block;
            width: 35px;
            height: 5px;
            background: white;
            margin: 6px 0;
            border-radius: 3px;
            transition: 0.3s;
        }

        /* Бокове меню */
        .sidebar {
            position: fixed;
            top: 0;
            right: -400px;
            width: 350px;
            height: 100vh;
            background: white;
            color: #333;
            padding: 80px 30px 30px;
            transition: 0.4s;
            z-index: 99;
            box-shadow: -5px 0 20px rgba(0,0,0,0.3);
            overflow-y: auto;
        }

        .sidebar.active {
            right: 0;
        }

        .sidebar h2 {
            color: #764ba2;
            margin-bottom: 30px;
            font-size: 28px;
        }

        .menu-item {
            margin-bottom: 40px;
        }

        .menu-item h3 {
            color: #667eea;
            font-size: 22px;
            margin-bottom: 15px;
            border-bottom: 2px solid #eee;
            padding-bottom: 8px;
        }

        .price-btn, .send-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 18px 25px;
            font-size: 18px;
            border-radius: 15px;
            cursor: pointer;
            width: 100%;
            margin: 10px 0;
            transition: transform 0.2s;
            font-weight: 600;
            letter-spacing: 1px;
            border: 1px solid rgba(255,255,255,0.3);
        }

        .send-btn {
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
        }

        .price-btn:hover, .send-btn:hover {
            transform: scale(1.02);
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
        }

        /* Затемнення фону */
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            display: none;
            z-index: 98;
        }

        .overlay.active {
            display: block;
        }

        /* Головний контент */
        .main-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: calc(100vh - 120px);
            padding: 20px;
            text-align: center;
        }

        .main-title {
            font-size: 48px;
            font-weight: 700;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .main-subtitle {
            font-size: 24px;
            margin-bottom: 50px;
            opacity: 0.95;
        }

        /* Кнопка Telegram */
        .telegram-btn {
            display: inline-flex;
            align-items: center;
            background: #0088cc;
            color: white;
            text-decoration: none;
            padding: 18px 40px;
            font-size: 24px;
            border-radius: 60px;
            margin-top: 30px;
            transition: 0.3s;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            font-weight: 600;
            border: 2px solid rgba(255,255,255,0.3);
        }

        .telegram-btn:hover {
            background: #0077b5;
            transform: scale(1.05);
            box-shadow: 0 15px 30px rgba(0,0,0,0.3);
        }

        .telegram-icon {
            width: 40px;
            height: 40px;
            background: white;
            border-radius: 50%;
            margin-right: 15px;
            position: relative;
        }

        .telegram-icon::before {
            content: "📱";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 24px;
        }

        /* Інформаційні блоки */
        .features {
            display: flex;
            gap: 30px;
            margin-top: 60px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .feature {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 25px;
            border-radius: 20px;
            width: 250px;
            border: 1px solid rgba(255,255,255,0.2);
        }

        .feature h3 {
            font-size: 22px;
            margin-bottom: 10px;
        }

        .close-btn {
            position: absolute;
            top: 20px;
            left: 20px;
            font-size: 30px;
            cursor: pointer;
            color: #999;
        }

        .close-btn:hover {
            color: #333;
        }

        /* Адаптація */
        @media (max-width: 768px) {
            .sidebar {
                width: 100%;
                right: -100%;
            }
            
            .main-title {
                font-size: 32px;
            }
            
            .site-title h1 {
                font-size: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Шапка сайту -->
    <div class="header">
        <div class="site-title">
            <h1>♻️ СКУПКА РАДІОДЕТАЛЕЙ</h1>
            <span> ПО ВСІЙ УКРАЇНІ</span>
        </div>
        
        <!-- Три палочки (бургер) -->
        <div class="menu-btn" id="menuBtn">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </div>

    <!-- Затемнення фону -->
    <div class="overlay" id="overlay"></div>

    <!-- Бокове меню -->
    <div class="sidebar" id="sidebar">
        <div class="close-btn" id="closeBtn">✖</div>
        <h2>📋 МЕНЮ</h2>
        
        <div class="menu-item">
            <h3>💰 ЦІНИ ТА ПРАЙС-ЛИСТ</h3>
            <button class="price-btn" onclick="alert('📋 Прайс-лист:\n\n• Мікросхеми - 500 грн/кг\n• Транзистори - 800 грн/кг\n• Конденсатори - 300 грн/кг\n• Роз'єми - 400 грн/кг\n• Плати - 250 грн/кг\n\nДля точної оцінки надішліть фото в Telegram!')">
                📄 ДИВИТИСЬ ПРАЙС
            </button>
        </div>
        
        <div class="menu-item">
            <h3>📦 КУДИ ВІДПРАВЛЯТИ</h3>
            <button class="send-btn" onclick="alert('🚚 АДРЕСА ДЛЯ ВІДПРАВЛЕННЯ:\n\nм. Київ, відділення Нова Пошта №123\nОтримувач: Скупка радіодеталей\nТелефон: +380 (XX) XXX-XX-XX\n\nАбо зв'яжіться з нами в Telegram для індивідуальних умов! 📱')">
                📬 ПОКАЗАТИ АДРЕСУ
            </button>
        </div>
        
        <div class="menu-item">
            <h3>📱 ЗВ'ЯЗОК</h3>
            <a href="https://t.me/eubzikkkkkkkkshvwhv" target="_blank" style="text-decoration: none;">
                <button class="price-btn" style="background: #0088cc;">💬 ТЕЛЕГРАМ ЧАТ</button>
            </a>
        </div>
    </div>

    <!-- Головний екран -->
    <div class="main-content">
        <h1 class="main-title">СКУПКА РАДІОДЕТАЛЕЙ</h1>
        <h2 class="main-subtitle">🇺🇦 ПО ВСІЙ УКРАЇНІ 🇺🇦</h2>
        
        <!-- Кнопка Telegram на головному екрані -->
        <a href="https://t.me/eubzikkkkkkkkshvwhv" target="_blank" class="telegram-btn">
            <span class="telegram-icon"></span>
            НАПИСАТИ НАМ У TELEGRAM
        </a>
        
        <!-- Особливості -->
        <div class="features">
            <div class="feature">
                <h3>💰 НАЙКРАЩІ ЦІНИ</h3>
                <p>Прайс-лист в меню ☝️</p>
            </div>
            <div class="feature">
                <h3>📦 ВІДПРАВЛЕННЯ</h3>
                <p>Нова Пошта по всій Україні</p>
            </div>
            <div class="feature">
                <h3>⚡ ШВИДКА ОПЛАТА</h3>
                <p>Готівка або переказ на карту</p>
            </div>
        </div>
    </div>

    <script>
        // Відкриття/закриття меню
        const menuBtn = document.getElementById('menuBtn');
        const sidebar = document.getElementById('sidebar');
        const overlay = document.getElementById('overlay');
        const closeBtn = document.getElementById('closeBtn');

        function openMenu() {
            sidebar.classList.add('active');
            overlay.classList.add('active');
        }

        function closeMenu() {
            sidebar.classList.remove('active');
            overlay.classList.remove('active');
        }

        menuBtn.addEventListener('click', openMenu);
        closeBtn.addEventListener('click', closeMenu);
        overlay.addEventListener('click', closeMenu);

        // Закриття по ESC
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape' && sidebar.classList.contains('active')) {
                closeMenu();
            }
        });
    </script>
</body>
</html># skupka-radio
