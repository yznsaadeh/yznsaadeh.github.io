# yznsaadeh.github.io
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة التمارين العلاجية</title>
    <!-- مكتبة لإنشاء الـ QR Code تلقائياً -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <style>
        * { box-sizing: border-box; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; padding: 0; }
        body { background-color: #f4f7f6; color: #333; padding: 20px; }
        header { text-align: center; margin-bottom: 30px; }
        header h1 { color: #2c3e50; font-size: 2rem; }
        header p { color: #7f8c8d; }
        
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .card {
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        
        .video-container {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
            height: 0;
            background: #000;
        }
        
        .video-container iframe {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            border: none;
        }
        
        .card-body { padding: 15px; flex: 1; display: flex; flex-direction: column; justify-content: space-between; }
        .card-title { font-size: 1.2rem; margin-bottom: 10px; color: #16a085; }
        .card-desc { font-size: 0.9rem; color: #666; margin-bottom: 15px; }
        
        .qr-section {
            border-top: 1px solid #eee;
            padding-top: 10px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .qr-text { font-size: 0.8rem; color: #888; }
        .qrcode { width: 64px; height: 64px; }
    </style>
</head>
<body>

    <header>
        <h1>المكتبة التفاعلية للتمارين العلاجية</h1>
        <p>اختر التمرين لمشاهدة الحركة أو امسح الـ QR الخاص به</p>
    </header>

    <div class="grid-container" id="exerciseGrid">
        <!-- التمارين تضاف هنا تلقائياً -->
    </div>

    <script>
        // قائمة التمارين (يمكنك تعديل الروابط والأسماء هنا)
        const exercises = [
            {
                title: "تمرين القيام والجلوس (Chair Squat)",
                desc: "تقوية عضلات الفخذين وتحسين التوازن لمرضى السكري.",
                videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ" // استبدل برابط الفيديو الخاص بك
            },
            {
                title: "تمرين دوران الكاحل (Ankle Circles)",
                desc: "تنشيط التروية الدموية في الأطراف السفلى وتقليل التنميل.",
                videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ"
            },
            {
                title: "تمرين الضغط على الجدار (Wall Push-ups)",
                desc: "تقوية الجزء العلوي من الجسم بطريقة آمنة.",
                videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ"
            }
        ];

        const container = document.getElementById('exerciseGrid');

        exercises.forEach((ex, index) => {
            const card = document.createElement('div');
            card.className = 'card';
            
            const qrId = `qrcode-${index}`;

            card.innerHTML = `
                <div class="video-container">
                    <iframe src="${ex.videoUrl}" allowfullscreen></iframe>
                </div>
                <div class="card-body">
                    <div>
                        <h3 class="card-title">${ex.title}</h3>
                        <p class="card-desc">${ex.desc}</p>
                    </div>
                    <div class="qr-section">
                        <span class="qr-text">امسح الرمز للفتح على الجوال</span>
                        <div id="${qrId}" class="qrcode"></div>
                    </div>
                </div>
            `;
            
            container.appendChild(card);

            // توليد QR Code لكل تمرين بناءً على رابط الفيديو
            new QRCode(document.getElementById(qrId), {
                text: ex.videoUrl,
                width: 64,
                height: 64
            });
        });
    </script>
</body>
</html>
