<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    * {
      font-family: 'Prompt', sans-serif;
    }
    .coin {
      animation: bounce 2s infinite;
    }
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    .sparkle {
      animation: sparkle 1.5s infinite;
    }
    @keyframes sparkle {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.5; transform: scale(1.2); }
    }
    .slide-in {
      animation: slideIn 0.5s ease-out;
    }
    @keyframes slideIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .correct-animation {
      animation: correctPop 0.5s ease-out;
    }
    @keyframes correctPop {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
    .shake {
      animation: shake 0.5s ease-out;
    }
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-10px); }
      75% { transform: translateX(10px); }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div id="app" class="h-full w-full overflow-auto" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"><!-- หน้าหลัก -->
   <div id="home-screen" class="min-h-full flex flex-col items-center justify-center p-6">
    <div class="text-center slide-in"><!-- ไอคอนเหรียญ -->
     <div class="coin mb-6">
      <svg width="120" height="120" viewbox="0 0 120 120" class="mx-auto drop-shadow-2xl"><circle cx="60" cy="60" r="55" fill="#FFD700" stroke="#DAA520" stroke-width="4" /> <circle cx="60" cy="60" r="45" fill="none" stroke="#DAA520" stroke-width="2" /> <text x="60" y="70" text-anchor="middle" font-size="36" font-weight="bold" fill="#B8860B">
        ฿
       </text>
      </svg>
     </div>
     <h1 id="main-title" class="text-4xl md:text-5xl font-bold text-white mb-4 drop-shadow-lg">คณิตศาสตร์การเงิน ป.5</h1>
     <p id="welcome-text" class="text-xl text-purple-100 mb-8">เรียนรู้เรื่องเงินอย่างสนุก! 🎉</p><!-- เมนูหลัก -->
     <div class="grid grid-cols-1 md:grid-cols-2 gap-4 max-w-2xl mx-auto"><button onclick="startLesson('coins')" class="bg-white/20 backdrop-blur-sm hover:bg-white/30 text-white p-6 rounded-2xl transition-all transform hover:scale-105 border border-white/30">
       <div class="text-4xl mb-3">
        🪙
       </div><h3 class="text-xl font-semibold">ชนิดของเงิน</h3><p class="text-purple-200 text-sm mt-1">เรียนรู้เหรียญและธนบัตร</p></button> <button onclick="startLesson('calculate')" class="bg-white/20 backdrop-blur-sm hover:bg-white/30 text-white p-6 rounded-2xl transition-all transform hover:scale-105 border border-white/30">
       <div class="text-4xl mb-3">
        🧮
       </div><h3 class="text-xl font-semibold">บวก-ลบเงิน</h3><p class="text-purple-200 text-sm mt-1">ฝึกคำนวณเงิน</p></button> <button onclick="startLesson('change')" class="bg-white/20 backdrop-blur-sm hover:bg-white/30 text-white p-6 rounded-2xl transition-all transform hover:scale-105 border border-white/30">
       <div class="text-4xl mb-3">
        💰
       </div><h3 class="text-xl font-semibold">การทอนเงิน</h3><p class="text-purple-200 text-sm mt-1">ฝึกทอนเงินจากการซื้อของ</p></button> <button onclick="startLesson('shopping')" class="bg-white/20 backdrop-blur-sm hover:bg-white/30 text-white p-6 rounded-2xl transition-all transform hover:scale-105 border border-white/30">
       <div class="text-4xl mb-3">
        🛒
       </div><h3 class="text-xl font-semibold">ซื้อของจำลอง</h3><p class="text-purple-200 text-sm mt-1">ลองซื้อของด้วยตัวเอง</p></button>
     </div><!-- แสดงคะแนน -->
     <div class="mt-8 bg-white/10 backdrop-blur-sm rounded-2xl p-4 inline-block border border-white/20">
      <p class="text-white text-lg">⭐ คะแนนรวม: <span id="total-score" class="font-bold text-yellow-300">0</span> คะแนน</p>
     </div><!-- ผู้สร้าง -->
     <div class="mt-6 bg-white/10 backdrop-blur-sm rounded-2xl p-4 inline-block border border-white/20">
      <p class="text-white text-sm">✨ สร้างโดย: <span class="font-semibold text-pink-200">เด็กหญิงกัณต์กมลศร</span></p>
      <p class="text-purple-200 text-xs mt-1">ชั้นประถมศึกษาปีที่ 5 MEP</p>
     </div>
    </div>
   </div><!-- หน้าบทเรียน: ชนิดของเงิน -->
   <div id="coins-screen" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="goHome()" class="text-white mb-6 flex items-center gap-2 hover:text-purple-200 transition-colors">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> กลับหน้าหลัก </button>
     <div class="bg-white rounded-3xl shadow-2xl p-8 slide-in">
      <h2 class="text-3xl font-bold text-purple-700 mb-6 text-center">🪙 ชนิดของเงินไทย</h2><!-- เหรียญ -->
      <div class="mb-8">
       <h3 class="text-xl font-semibold text-purple-600 mb-4">เหรียญกษาปณ์</h3>
       <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
        <div class="text-center p-4 bg-gradient-to-br from-amber-100 to-amber-200 rounded-2xl">
         <div class="w-12 h-12 mx-auto bg-gradient-to-br from-amber-400 to-amber-600 rounded-full flex items-center justify-center text-white font-bold shadow-lg">
          25
         </div>
         <p class="mt-2 font-medium text-amber-800">25 สตางค์</p>
        </div>
        <div class="text-center p-4 bg-gradient-to-br from-amber-100 to-amber-200 rounded-2xl">
         <div class="w-14 h-14 mx-auto bg-gradient-to-br from-amber-400 to-amber-600 rounded-full flex items-center justify-center text-white font-bold shadow-lg">
          50
         </div>
         <p class="mt-2 font-medium text-amber-800">50 สตางค์</p>
        </div>
        <div class="text-center p-4 bg-gradient-to-br from-gray-100 to-gray-200 rounded-2xl">
         <div class="w-14 h-14 mx-auto bg-gradient-to-br from-gray-300 to-gray-500 rounded-full flex items-center justify-center text-white font-bold shadow-lg">
          1
         </div>
         <p class="mt-2 font-medium text-gray-700">1 บาท</p>
        </div>
        <div class="text-center p-4 bg-gradient-to-br from-gray-100 to-gray-200 rounded-2xl">
         <div class="w-16 h-16 mx-auto bg-gradient-to-br from-gray-300 to-gray-500 rounded-full flex items-center justify-center text-white font-bold shadow-lg">
          2
         </div>
         <p class="mt-2 font-medium text-gray-700">2 บาท</p>
        </div>
        <div class="text-center p-4 bg-gradient-to-br from-gray-100 to-gray-200 rounded-2xl">
         <div class="w-18 h-18 mx-auto bg-gradient-to-br from-gray-400 to-gray-600 rounded-full flex items-center justify-center text-white font-bold shadow-lg text-lg" style="width: 4.5rem; height: 4.5rem;">
          5
         </div>
         <p class="mt-2 font-medium text-gray-700">5 บาท</p>
        </div>
        <div class="text-center p-4 bg-gradient-to-br from-yellow-100 to-yellow-200 rounded-2xl col-span-2 md:col-span-5 md:w-1/3 md:mx-auto">
         <div class="w-20 h-20 mx-auto rounded-full flex items-center justify-center text-white font-bold shadow-lg text-xl" style="background: linear-gradient(135deg, #C0C0C0 50%, #FFD700 50%);">
          10
         </div>
         <p class="mt-2 font-medium text-yellow-800">10 บาท (สองสี)</p>
        </div>
       </div>
      </div><!-- ธนบัตร -->
      <div class="mb-8">
       <h3 class="text-xl font-semibold text-purple-600 mb-4">ธนบัตร</h3>
       <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        <div class="p-4 bg-gradient-to-r from-green-400 to-green-600 rounded-xl text-white">
         <div class="text-3xl font-bold">
          ฿20
         </div>
         <p class="text-green-100">ธนบัตรสีเขียว</p>
        </div>
        <div class="p-4 bg-gradient-to-r from-purple-400 to-purple-600 rounded-xl text-white">
         <div class="text-3xl font-bold">
          ฿50
         </div>
         <p class="text-purple-100">ธนบัตรสีม่วง</p>
        </div>
        <div class="p-4 bg-gradient-to-r from-red-400 to-red-600 rounded-xl text-white">
         <div class="text-3xl font-bold">
          ฿100
         </div>
         <p class="text-red-100">ธนบัตรสีแดง</p>
        </div>
        <div class="p-4 bg-gradient-to-r from-blue-400 to-blue-600 rounded-xl text-white">
         <div class="text-3xl font-bold">
          ฿500
         </div>
         <p class="text-blue-100">ธนบัตรสีน้ำเงิน</p>
        </div>
        <div class="p-4 bg-gradient-to-r from-amber-400 to-amber-600 rounded-xl text-white md:col-span-2 lg:col-span-1">
         <div class="text-3xl font-bold">
          ฿1,000
         </div>
         <p class="text-amber-100">ธนบัตรสีน้ำตาล</p>
        </div>
       </div>
      </div><!-- ข้อควรรู้ -->
      <div class="bg-purple-50 rounded-2xl p-6">
       <h3 class="text-lg font-semibold text-purple-700 mb-3">💡 ข้อควรรู้</h3>
       <ul class="space-y-2 text-purple-600">
        <li>• 100 สตางค์ = 1 บาท</li>
        <li>• 4 เหรียญ 25 สตางค์ = 1 บาท</li>
        <li>• 2 เหรียญ 50 สตางค์ = 1 บาท</li>
       </ul>
      </div><button onclick="startQuiz('coins')" class="w-full mt-6 bg-gradient-to-r from-purple-500 to-pink-500 text-white py-4 rounded-2xl font-semibold text-lg hover:from-purple-600 hover:to-pink-600 transition-all transform hover:scale-105"> 🎯 ทดสอบความเข้าใจ </button>
     </div>
    </div>
   </div><!-- หน้าบทเรียน: บวก-ลบเงิน -->
   <div id="calculate-screen" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="goHome()" class="text-white mb-6 flex items-center gap-2 hover:text-purple-200 transition-colors">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> กลับหน้าหลัก </button>
     <div class="bg-white rounded-3xl shadow-2xl p-8 slide-in">
      <h2 class="text-3xl font-bold text-purple-700 mb-6 text-center">🧮 บวก-ลบเงิน</h2>
      <div id="calc-question" class="text-center mb-8">
       <p class="text-lg text-gray-600 mb-4" id="calc-story"></p>
       <div class="text-4xl font-bold text-purple-700 mb-6" id="calc-problem"></div>
       <div class="flex justify-center gap-4 flex-wrap"><input type="number" id="calc-answer" class="w-40 text-center text-2xl p-4 border-4 border-purple-300 rounded-2xl focus:border-purple-500 focus:outline-none" placeholder="?"> <span class="text-2xl font-bold text-purple-700 self-center">บาท</span>
       </div><button onclick="checkCalcAnswer()" class="mt-6 bg-gradient-to-r from-green-400 to-green-600 text-white px-8 py-4 rounded-2xl font-semibold text-lg hover:from-green-500 hover:to-green-700 transition-all"> ✓ ตรวจคำตอบ </button>
      </div>
      <div id="calc-feedback" class="hidden text-center py-6 rounded-2xl mb-6"></div>
      <div class="flex justify-between items-center bg-purple-50 rounded-2xl p-4"><span class="text-purple-700">ข้อที่: <span id="calc-current">1</span>/5</span> <span class="text-purple-700">คะแนน: <span id="calc-score">0</span></span>
      </div>
     </div>
    </div>
   </div><!-- หน้าบทเรียน: การทอนเงิน -->
   <div id="change-screen" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="goHome()" class="text-white mb-6 flex items-center gap-2 hover:text-purple-200 transition-colors">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> กลับหน้าหลัก </button>
     <div class="bg-white rounded-3xl shadow-2xl p-8 slide-in">
      <h2 class="text-3xl font-bold text-purple-700 mb-6 text-center">💰 การทอนเงิน</h2>
      <div id="change-question" class="text-center mb-8">
       <div class="bg-gradient-to-r from-amber-100 to-orange-100 rounded-2xl p-6 mb-6">
        <p class="text-lg text-amber-800" id="change-story"></p>
       </div>
       <div class="grid grid-cols-3 gap-4 mb-6">
        <div class="bg-purple-50 rounded-xl p-4">
         <p class="text-gray-600 text-sm">ราคาสินค้า</p>
         <p class="text-2xl font-bold text-purple-700" id="change-price"></p>
        </div>
        <div class="bg-green-50 rounded-xl p-4">
         <p class="text-gray-600 text-sm">จ่ายเงิน</p>
         <p class="text-2xl font-bold text-green-600" id="change-paid"></p>
        </div>
        <div class="bg-pink-50 rounded-xl p-4">
         <p class="text-gray-600 text-sm">ต้องทอน</p>
         <p class="text-2xl font-bold text-pink-600">?</p>
        </div>
       </div>
       <div class="flex justify-center gap-4 flex-wrap"><input type="number" id="change-answer" class="w-40 text-center text-2xl p-4 border-4 border-purple-300 rounded-2xl focus:border-purple-500 focus:outline-none" placeholder="?"> <span class="text-2xl font-bold text-purple-700 self-center">บาท</span>
       </div><button onclick="checkChangeAnswer()" class="mt-6 bg-gradient-to-r from-green-400 to-green-600 text-white px-8 py-4 rounded-2xl font-semibold text-lg hover:from-green-500 hover:to-green-700 transition-all"> ✓ ตรวจคำตอบ </button>
      </div>
      <div id="change-feedback" class="hidden text-center py-6 rounded-2xl mb-6"></div>
      <div class="flex justify-between items-center bg-purple-50 rounded-2xl p-4"><span class="text-purple-700">ข้อที่: <span id="change-current">1</span>/5</span> <span class="text-purple-700">คะแนน: <span id="change-score">0</span></span>
      </div>
     </div>
    </div>
   </div><!-- หน้าซื้อของจำลอง -->
   <div id="shopping-screen" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="goHome()" class="text-white mb-6 flex items-center gap-2 hover:text-purple-200 transition-colors">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> กลับหน้าหลัก </button>
     <div class="bg-white rounded-3xl shadow-2xl p-8 slide-in">
      <h2 class="text-3xl font-bold text-purple-700 mb-6 text-center">🛒 ร้านค้าจำลอง</h2><!-- กระเป๋าเงิน -->
      <div class="bg-gradient-to-r from-green-400 to-green-600 rounded-2xl p-6 mb-6 text-white text-center">
       <p class="text-lg">💼 เงินในกระเป๋า</p>
       <p class="text-4xl font-bold mt-2" id="wallet-amount">100 บาท</p>
      </div><!-- สินค้า -->
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
       <div class="bg-gradient-to-br from-pink-50 to-pink-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('ดินสอ', 5)">
        <div class="text-4xl mb-2">
         ✏️
        </div>
        <p class="font-medium text-gray-700">ดินสอ</p>
        <p class="text-pink-600 font-bold">฿5</p>
       </div>
       <div class="bg-gradient-to-br from-blue-50 to-blue-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('ยางลบ', 8)">
        <div class="text-4xl mb-2">
         🧽
        </div>
        <p class="font-medium text-gray-700">ยางลบ</p>
        <p class="text-blue-600 font-bold">฿8</p>
       </div>
       <div class="bg-gradient-to-br from-yellow-50 to-yellow-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('สมุด', 15)">
        <div class="text-4xl mb-2">
         📓
        </div>
        <p class="font-medium text-gray-700">สมุด</p>
        <p class="text-yellow-600 font-bold">฿15</p>
       </div>
       <div class="bg-gradient-to-br from-purple-50 to-purple-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('ไม้บรรทัด', 12)">
        <div class="text-4xl mb-2">
         📏
        </div>
        <p class="font-medium text-gray-700">ไม้บรรทัด</p>
        <p class="text-purple-600 font-bold">฿12</p>
       </div>
       <div class="bg-gradient-to-br from-red-50 to-red-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('กาว', 18)">
        <div class="text-4xl mb-2">
         🧴
        </div>
        <p class="font-medium text-gray-700">กาว</p>
        <p class="text-red-600 font-bold">฿18</p>
       </div>
       <div class="bg-gradient-to-br from-green-50 to-green-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('กรรไกร', 25)">
        <div class="text-4xl mb-2">
         ✂️
        </div>
        <p class="font-medium text-gray-700">กรรไกร</p>
        <p class="text-green-600 font-bold">฿25</p>
       </div>
       <div class="bg-gradient-to-br from-orange-50 to-orange-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('สีไม้', 35)">
        <div class="text-4xl mb-2">
         🖍️
        </div>
        <p class="font-medium text-gray-700">สีไม้</p>
        <p class="text-orange-600 font-bold">฿35</p>
       </div>
       <div class="bg-gradient-to-br from-cyan-50 to-cyan-100 rounded-2xl p-4 text-center cursor-pointer hover:shadow-lg transition-all" onclick="addToCart('กระเป๋าดินสอ', 45)">
        <div class="text-4xl mb-2">
         👝
        </div>
        <p class="font-medium text-gray-700">กระเป๋าดินสอ</p>
        <p class="text-cyan-600 font-bold">฿45</p>
       </div>
      </div><!-- ตะกร้า -->
      <div class="bg-gray-50 rounded-2xl p-6">
       <h3 class="text-xl font-semibold text-gray-700 mb-4">🛍️ ตะกร้าสินค้า</h3>
       <div id="cart-items" class="space-y-2 mb-4 min-h-[60px]">
        <p class="text-gray-400 text-center py-4">ยังไม่มีสินค้าในตะกร้า</p>
       </div>
       <div class="border-t-2 border-gray-200 pt-4 flex justify-between items-center"><span class="text-xl font-bold text-gray-700">รวมทั้งหมด:</span> <span class="text-2xl font-bold text-purple-600" id="cart-total">฿0</span>
       </div>
       <div class="flex gap-4 mt-4"><button onclick="clearCart()" class="flex-1 bg-gray-200 text-gray-700 py-3 rounded-xl font-semibold hover:bg-gray-300 transition-colors"> ล้างตะกร้า </button> <button onclick="checkout()" class="flex-1 bg-gradient-to-r from-purple-500 to-pink-500 text-white py-3 rounded-xl font-semibold hover:from-purple-600 hover:to-pink-600 transition-all"> จ่ายเงิน </button>
       </div>
      </div>
      <div id="shopping-feedback" class="hidden text-center py-6 rounded-2xl mt-6"></div>
     </div>
    </div>
   </div><!-- หน้า Quiz -->
   <div id="quiz-screen" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="goHome()" class="text-white mb-6 flex items-center gap-2 hover:text-purple-200 transition-colors">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> กลับหน้าหลัก </button>
     <div class="bg-white rounded-3xl shadow-2xl p-8 slide-in">
      <h2 class="text-2xl font-bold text-purple-700 mb-6 text-center" id="quiz-title">ทดสอบความเข้าใจ</h2>
      <div id="quiz-content" class="text-center">
       <p class="text-xl text-gray-700 mb-6" id="quiz-question"></p>
       <div id="quiz-options" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
      </div>
      <div id="quiz-feedback" class="hidden text-center py-6 rounded-2xl mt-6"></div>
      <div class="flex justify-between items-center bg-purple-50 rounded-2xl p-4 mt-6"><span class="text-purple-700">ข้อที่: <span id="quiz-current">1</span>/5</span> <span class="text-purple-700">คะแนน: <span id="quiz-score">0</span></span>
      </div>
     </div>
    </div>
   </div><!-- หน้าผลลัพธ์ -->
   <div id="result-screen" class="hidden min-h-full flex items-center justify-center p-6">
    <div class="bg-white rounded-3xl shadow-2xl p-8 max-w-md w-full text-center slide-in">
     <div class="text-6xl mb-6" id="result-emoji">
      🎉
     </div>
     <h2 class="text-3xl font-bold text-purple-700 mb-4" id="result-title">ยอดเยี่ยม!</h2>
     <p class="text-xl text-gray-600 mb-6" id="result-message"></p>
     <div class="bg-gradient-to-r from-yellow-100 to-amber-100 rounded-2xl p-6 mb-6">
      <p class="text-gray-600">คะแนนที่ได้</p>
      <p class="text-5xl font-bold text-amber-600" id="result-score">0/5</p>
     </div><button onclick="goHome()" class="w-full bg-gradient-to-r from-purple-500 to-pink-500 text-white py-4 rounded-2xl font-semibold text-lg hover:from-purple-600 hover:to-pink-600 transition-all"> 🏠 กลับหน้าหลัก </button>
    </div>
   </div>
  </div>
  <script>
    // Default configuration
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน ป.5',
      welcome_message: 'เรียนรู้เรื่องเงินอย่างสนุก!',
      background_color: '#667eea',
      surface_color: '#ffffff',
      text_color: '#6b21a8',
      primary_action_color: '#a855f7',
      secondary_action_color: '#ec4899',
      font_family: 'Prompt',
      font_size: 16
    };

    let config = { ...defaultConfig };
    let totalScore = 0;
    let currentQuiz = null;
    let quizScore = 0;
    let quizCurrent = 0;
    let quizQuestions = [];
    
    // Calculate questions
    let calcScore = 0;
    let calcCurrent = 0;
    let calcAnswer = 0;
    let calcQuestions = [];
    
    // Change questions
    let changeScore = 0;
    let changeCurrent = 0;
    let changeAnswer = 0;
    let changeQuestions = [];
    
    // Shopping
    let wallet = 100;
    let cart = [];
    let cartTotal = 0;

    // Initialize Element SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (newConfig) => {
          config = { ...defaultConfig, ...newConfig };
          updateUI();
        },
        mapToCapabilities: (cfg) => ({
          recolorables: [
            {
              get: () => cfg.background_color || defaultConfig.background_color,
              set: (value) => {
                cfg.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => cfg.surface_color || defaultConfig.surface_color,
              set: (value) => {
                cfg.surface_color = value;
                window.elementSdk.setConfig({ surface_color: value });
              }
            },
            {
              get: () => cfg.text_color || defaultConfig.text_color,
              set: (value) => {
                cfg.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            },
            {
              get: () => cfg.primary_action_color || defaultConfig.primary_action_color,
              set: (value) => {
                cfg.primary_action_color = value;
                window.elementSdk.setConfig({ primary_action_color: value });
              }
            },
            {
              get: () => cfg.secondary_action_color || defaultConfig.secondary_action_color,
              set: (value) => {
                cfg.secondary_action_color = value;
                window.elementSdk.setConfig({ secondary_action_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => cfg.font_family || defaultConfig.font_family,
            set: (value) => {
              cfg.font_family = value;
              window.elementSdk.setConfig({ font_family: value });
            }
          },
          fontSizeable: {
            get: () => cfg.font_size || defaultConfig.font_size,
            set: (value) => {
              cfg.font_size = value;
              window.elementSdk.setConfig({ font_size: value });
            }
          }
        }),
        mapToEditPanelValues: (cfg) => new Map([
          ['app_title', cfg.app_title || defaultConfig.app_title],
          ['welcome_message', cfg.welcome_message || defaultConfig.welcome_message]
        ])
      });
    }

    function updateUI() {
      const appTitle = config.app_title || defaultConfig.app_title;
      const welcomeMessage = config.welcome_message || defaultConfig.welcome_message;
      const bgColor = config.background_color || defaultConfig.background_color;
      const surfaceColor = config.surface_color || defaultConfig.surface_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const primaryAction = config.primary_action_color || defaultConfig.primary_action_color;
      const secondaryAction = config.secondary_action_color || defaultConfig.secondary_action_color;
      const fontFamily = config.font_family || defaultConfig.font_family;
      const fontSize = config.font_size || defaultConfig.font_size;

      // Update text content
      document.getElementById('main-title').textContent = appTitle;
      document.getElementById('welcome-text').textContent = welcomeMessage + ' 🎉';

      // Update colors
      const app = document.getElementById('app');
      app.style.background = `linear-gradient(135deg, ${bgColor} 0%, ${secondaryAction} 100%)`;

      // Update font
      document.body.style.fontFamily = `${fontFamily}, sans-serif`;
      
      // Update font sizes
      document.getElementById('main-title').style.fontSize = `${fontSize * 2.5}px`;
      document.getElementById('welcome-text').style.fontSize = `${fontSize * 1.25}px`;
    }

    function showScreen(screenId) {
      const screens = ['home-screen', 'coins-screen', 'calculate-screen', 'change-screen', 'shopping-screen', 'quiz-screen', 'result-screen'];
      screens.forEach(id => {
        document.getElementById(id).classList.add('hidden');
      });
      document.getElementById(screenId).classList.remove('hidden');
    }

    function goHome() {
      showScreen('home-screen');
      document.getElementById('total-score').textContent = totalScore;
    }

    function startLesson(type) {
      if (type === 'coins') {
        showScreen('coins-screen');
      } else if (type === 'calculate') {
        showScreen('calculate-screen');
        initCalcQuestions();
      } else if (type === 'change') {
        showScreen('change-screen');
        initChangeQuestions();
      } else if (type === 'shopping') {
        showScreen('shopping-screen');
        resetShopping();
      }
    }

    // Calculate questions
    function initCalcQuestions() {
      calcScore = 0;
      calcCurrent = 0;
      calcQuestions = generateCalcQuestions();
      showCalcQuestion();
    }

    function generateCalcQuestions() {
      const questions = [];
      const stories = [
        { template: 'น้องมีเงิน {a} บาท ได้รับจากแม่อีก {b} บาท รวมมีเงินเท่าไร?', op: '+' },
        { template: 'พี่มีเงิน {a} บาท ซื้อขนมไป {b} บาท เหลือเงินเท่าไร?', op: '-' },
        { template: 'เด็กชายมีเงินออม {a} บาท ออมเพิ่มอีก {b} บาท รวมออมได้เท่าไร?', op: '+' },
        { template: 'คุณแม่มีเงิน {a} บาท จ่ายค่าน้ำไป {b} บาท เหลือเงินเท่าไร?', op: '-' },
        { template: 'น้องได้รับเงินวันจันทร์ {a} บาท วันอังคาร {b} บาท รวมได้เท่าไร?', op: '+' }
      ];
      
      for (let i = 0; i < 5; i++) {
        const story = stories[i];
        let a, b, answer;
        if (story.op === '+') {
          a = Math.floor(Math.random() * 90) + 10;
          b = Math.floor(Math.random() * 90) + 10;
          answer = a + b;
        } else {
          a = Math.floor(Math.random() * 90) + 50;
          b = Math.floor(Math.random() * (a - 10)) + 5;
          answer = a - b;
        }
        questions.push({
          story: story.template.replace('{a}', a).replace('{b}', b),
          problem: `${a} ${story.op} ${b} = ?`,
          answer
        });
      }
      return questions;
    }

    function showCalcQuestion() {
      if (calcCurrent >= calcQuestions.length) {
        showResult('calculate', calcScore, calcQuestions.length);
        return;
      }
      
      const q = calcQuestions[calcCurrent];
      document.getElementById('calc-story').textContent = q.story;
      document.getElementById('calc-problem').textContent = q.problem;
      document.getElementById('calc-answer').value = '';
      document.getElementById('calc-current').textContent = calcCurrent + 1;
      document.getElementById('calc-score').textContent = calcScore;
      document.getElementById('calc-feedback').classList.add('hidden');
      calcAnswer = q.answer;
    }

    function checkCalcAnswer() {
      const userAnswer = parseInt(document.getElementById('calc-answer').value);
      const feedback = document.getElementById('calc-feedback');
      
      if (isNaN(userAnswer)) {
        feedback.innerHTML = '⚠️ กรุณาใส่คำตอบ';
        feedback.className = 'text-center py-6 rounded-2xl mb-6 bg-yellow-100 text-yellow-700';
        feedback.classList.remove('hidden');
        return;
      }
      
      if (userAnswer === calcAnswer) {
        calcScore++;
        totalScore++;
        feedback.innerHTML = '✅ ถูกต้อง! เก่งมาก!';
        feedback.className = 'text-center py-6 rounded-2xl mb-6 bg-green-100 text-green-700 correct-animation';
      } else {
        feedback.innerHTML = `❌ ไม่ถูกต้อง คำตอบที่ถูกคือ ${calcAnswer} บาท`;
        feedback.className = 'text-center py-6 rounded-2xl mb-6 bg-red-100 text-red-700 shake';
      }
      feedback.classList.remove('hidden');
      
      setTimeout(() => {
        calcCurrent++;
        showCalcQuestion();
      }, 1500);
    }

    // Change questions
    function initChangeQuestions() {
      changeScore = 0;
      changeCurrent = 0;
      changeQuestions = generateChangeQuestions();
      showChangeQuestion();
    }

    function generateChangeQuestions() {
      const questions = [];
      const items = [
        { name: 'ลูกอม', emoji: '🍬' },
        { name: 'น้ำ', emoji: '💧' },
        { name: 'ขนมปัง', emoji: '🍞' },
        { name: 'นม', emoji: '🥛' },
        { name: 'ไอศกรีม', emoji: '🍦' }
      ];
      
      for (let i = 0; i < 5; i++) {
        const item = items[i];
        const price = Math.floor(Math.random() * 80) + 15;
        const paid = Math.ceil(price / 10) * 10 + (Math.floor(Math.random() * 3) * 10);
        const change = paid - price;
        questions.push({
          story: `ซื้อ${item.name} ${item.emoji} ราคา ${price} บาท จ่ายเงิน ${paid} บาท`,
          price,
          paid,
          answer: change
        });
      }
      return questions;
    }

    function showChangeQuestion() {
      if (changeCurrent >= changeQuestions.length) {
        showResult('change', changeScore, changeQuestions.length);
        return;
      }
      
      const q = changeQuestions[changeCurrent];
      document.getElementById('change-story').textContent = q.story;
      document.getElementById('change-price').textContent = `฿${q.price}`;
      document.getElementById('change-paid').textContent = `฿${q.paid}`;
      document.getElementById('change-answer').value = '';
      document.getElementById('change-current').textContent = changeCurrent + 1;
      document.getElementById('change-score').textContent = changeScore;
      document.getElementById('change-feedback').classList.add('hidden');
      changeAnswer = q.answer;
    }

    function checkChangeAnswer() {
      const userAnswer = parseInt(document.getElementById('change-answer').value);
      const feedback = document.getElementById('change-feedback');
      
      if (isNaN(userAnswer)) {
        feedback.innerHTML = '⚠️ กรุณาใส่คำตอบ';
        feedback.className = 'text-center py-6 rounded-2xl mb-6 bg-yellow-100 text-yellow-700';
        feedback.classList.remove('hidden');
        return;
      }
      
      if (userAnswer === changeAnswer) {
        changeScore++;
        totalScore++;
        feedback.innerHTML = '✅ ถูกต้อง! เก่งมาก!';
        feedback.className = 'text-center py-6 rounded-2xl mb-6 bg-green-100 text-green-700 correct-animation';
      } else {
        feedback.innerHTML = `❌ ไม่ถูกต้อง ต้องทอน ${changeAnswer} บาท`;
        feedback.className = 'text-center py-6 rounded-2xl mb-6 bg-red-100 text-red-700 shake';
      }
      feedback.classList.remove('hidden');
      
      setTimeout(() => {
        changeCurrent++;
        showChangeQuestion();
      }, 1500);
    }

    // Shopping
    function resetShopping() {
      wallet = 100;
      cart = [];
      cartTotal = 0;
      updateShoppingUI();
      document.getElementById('shopping-feedback').classList.add('hidden');
    }

    function updateShoppingUI() {
      document.getElementById('wallet-amount').textContent = `${wallet} บาท`;
      document.getElementById('cart-total').textContent = `฿${cartTotal}`;
      
      const cartEl = document.getElementById('cart-items');
      if (cart.length === 0) {
        cartEl.innerHTML = '<p class="text-gray-400 text-center py-4">ยังไม่มีสินค้าในตะกร้า</p>';
      } else {
        cartEl.innerHTML = cart.map((item, index) => `
          <div class="flex justify-between items-center bg-white rounded-lg p-3 border border-gray-200">
            <span>${item.name}</span>
            <div class="flex items-center gap-2">
              <span class="font-bold text-purple-600">฿${item.price}</span>
              <button onclick="removeFromCart(${index})" class="text-red-500 hover:text-red-700">✕</button>
            </div>
          </div>
        `).join('');
      }
    }

    function addToCart(name, price) {
      cart.push({ name, price });
      cartTotal += price;
      updateShoppingUI();
    }

    function removeFromCart(index) {
      cartTotal -= cart[index].price;
      cart.splice(index, 1);
      updateShoppingUI();
    }

    function clearCart() {
      cart = [];
      cartTotal = 0;
      updateShoppingUI();
    }

    function checkout() {
      const feedback = document.getElementById('shopping-feedback');
      
      if (cart.length === 0) {
        feedback.innerHTML = '⚠️ กรุณาเลือกสินค้าก่อน';
        feedback.className = 'text-center py-6 rounded-2xl mt-6 bg-yellow-100 text-yellow-700';
        feedback.classList.remove('hidden');
        return;
      }
      
      if (cartTotal > wallet) {
        feedback.innerHTML = `❌ เงินไม่พอ! ต้องการ ฿${cartTotal} แต่มีเพียง ฿${wallet}`;
        feedback.className = 'text-center py-6 rounded-2xl mt-6 bg-red-100 text-red-700 shake';
        feedback.classList.remove('hidden');
        return;
      }
      
      const change = wallet - cartTotal;
      wallet = change;
      totalScore += 5;
      
      feedback.innerHTML = `
        <div class="correct-animation">
          ✅ จ่ายเงินสำเร็จ!<br>
          <span class="text-2xl font-bold">ทอน ${change} บาท</span><br>
          <span class="text-sm text-gray-500">+5 คะแนน</span>
        </div>
      `;
      feedback.className = 'text-center py-6 rounded-2xl mt-6 bg-green-100 text-green-700';
      feedback.classList.remove('hidden');
      
      cart = [];
      cartTotal = 0;
      updateShoppingUI();
    }

    // Quiz
    function startQuiz(type) {
      currentQuiz = type;
      quizScore = 0;
      quizCurrent = 0;
      quizQuestions = generateQuizQuestions(type);
      showScreen('quiz-screen');
      showQuizQuestion();
    }

    function generateQuizQuestions(type) {
      if (type === 'coins') {
        return [
          {
            question: 'เหรียญ 10 บาท มีลักษณะอย่างไร?',
            options: ['สีทอง', 'สีเงิน', 'สองสี (ทองและเงิน)', 'สีทองแดง'],
            answer: 2
          },
          {
            question: '100 สตางค์ เท่ากับกี่บาท?',
            options: ['10 บาท', '1 บาท', '0.5 บาท', '5 บาท'],
            answer: 1
          },
          {
            question: 'ธนบัตรสีเขียวมีมูลค่าเท่าไร?',
            options: ['50 บาท', '100 บาท', '20 บาท', '500 บาท'],
            answer: 2
          },
          {
            question: 'เหรียญ 25 สตางค์ กี่เหรียญรวมกันได้ 1 บาท?',
            options: ['2 เหรียญ', '4 เหรียญ', '5 เหรียญ', '10 เหรียญ'],
            answer: 1
          },
          {
            question: 'ธนบัตรใบละ 1,000 บาท เป็นสีอะไร?',
            options: ['สีแดง', 'สีน้ำเงิน', 'สีม่วง', 'สีน้ำตาล'],
            answer: 3
          }
        ];
      }
      return [];
    }

    function showQuizQuestion() {
      if (quizCurrent >= quizQuestions.length) {
        showResult('quiz', quizScore, quizQuestions.length);
        return;
      }
      
      const q = quizQuestions[quizCurrent];
      document.getElementById('quiz-question').textContent = q.question;
      document.getElementById('quiz-current').textContent = quizCurrent + 1;
      document.getElementById('quiz-score').textContent = quizScore;
      document.getElementById('quiz-feedback').classList.add('hidden');
      
      const optionsEl = document.getElementById('quiz-options');
      optionsEl.innerHTML = q.options.map((opt, i) => `
        <button onclick="checkQuizAnswer(${i})" class="bg-gradient-to-r from-purple-100 to-pink-100 hover:from-purple-200 hover:to-pink-200 text-purple-700 p-4 rounded-2xl font-medium text-lg transition-all transform hover:scale-105">
          ${opt}
        </button>
      `).join('');
    }

    function checkQuizAnswer(selected) {
      const q = quizQuestions[quizCurrent];
      const feedback = document.getElementById('quiz-feedback');
      
      if (selected === q.answer) {
        quizScore++;
        totalScore++;
        feedback.innerHTML = '✅ ถูกต้อง! เก่งมาก!';
        feedback.className = 'text-center py-6 rounded-2xl mt-6 bg-green-100 text-green-700 correct-animation';
      } else {
        feedback.innerHTML = `❌ ไม่ถูกต้อง คำตอบที่ถูกคือ "${q.options[q.answer]}"`;
        feedback.className = 'text-center py-6 rounded-2xl mt-6 bg-red-100 text-red-700 shake';
      }
      feedback.classList.remove('hidden');
      
      setTimeout(() => {
        quizCurrent++;
        showQuizQuestion();
      }, 1500);
    }

    function showResult(type, score, total) {
      showScreen('result-screen');
      
      const percentage = (score / total) * 100;
      let emoji, title, message;
      
      if (percentage === 100) {
        emoji = '🏆';
        title = 'ยอดเยี่ยมมาก!';
        message = 'ตอบถูกทุกข้อ! คุณเก่งที่สุด!';
      } else if (percentage >= 80) {
        emoji = '🎉';
        title = 'เก่งมาก!';
        message = 'ทำได้ดีมากเลย!';
      } else if (percentage >= 60) {
        emoji = '😊';
        title = 'ดีมาก!';
        message = 'พยายามอีกนิดนะ!';
      } else {
        emoji = '💪';
        title = 'พยายามต่อไป!';
        message = 'ลองทบทวนและทำใหม่อีกครั้งนะ';
      }
      
      document.getElementById('result-emoji').textContent = emoji;
      document.getElementById('result-title').textContent = title;
      document.getElementById('result-message').textContent = message;
      document.getElementById('result-score').textContent = `${score}/${total}`;
    }

    // Initialize
    updateUI();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c032169773e7322',t:'MTc2ODc5MjEzOC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
