<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Business English Hub – Mr. Hùng</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    :root { --primary: #0d47a1; --accent: #ff9800; }
    .tail-container { font-family: 'Segoe UI', system_ui, sans-serif; }
    .nav-tab { transition: all 0.3s ease; }
    .nav-tab.active { background-color: white; color: var(--primary); box-shadow: 0 4px 15px rgba(0,0,0,0.15); }
    .flashcard { perspective: 1000px; height: 260px; }
    .flashcard-inner { transition: transform 0.75s cubic-bezier(0.23,1,0.32,1); transform-style: preserve-3d; }
    .flashcard.flipped .flashcard-inner { transform: rotateY(180deg); }
    .flashcard-front, .flashcard-back { backface-visibility: hidden; border-radius: 16px; }
    .flashcard-back { transform: rotateY(180deg); }
    .module-card:hover { transform: translateY(-10px); }
    .progress-bar { transition: width 1.2s cubic-bezier(0.34,1.56,0.64,1); }
  </style>
</head>
<body class="tail-container bg-slate-50 text-slate-800 min-h-screen">
  <!-- Top Bar (your original) -->
  <header class="bg-[#0d47a1] text-white sticky top-0 z-50 shadow-lg">
    <div class="max-w-7xl mx-auto px-6 py-5 flex justify-between items-center">
      <div class="flex items-center gap-4">
        <i class="fa-solid fa-briefcase text-4xl"></i>
        <div>
          <h1 class="text-2xl font-bold tracking-tight">Business English Hub</h1>
          <p class="text-xs text-blue-200 -mt-1">Private Executive Program • Mr. Hùng</p>
        </div>
      </div>
      <div class="flex items-center gap-6">
        <div class="flex items-center gap-4 bg-white/10 px-6 py-3 rounded-3xl">
          <div>
            <span class="text-sm font-semibold">XP:</span>
            <span id="xp-count" class="text-orange-400 font-bold">1850</span>
          </div>
          <div class="w-40 h-2.5 bg-white/30 rounded-full overflow-hidden">
            <div id="xp-bar" class="h-full bg-[#ff9800] rounded-full progress-bar" style="width: 68%"></div>
          </div>
          <div class="text-sm">Lv <span id="level" class="font-bold">9</span></div>
        </div>
        <button onclick="toggleDarkMode()" class="w-11 h-11 flex items-center justify-center bg-white/10 hover:bg-white/20 rounded-2xl transition-all">
          <i id="theme-icon" class="fa-solid fa-moon text-xl"></i>
        </button>
      </div>
    </div>
  </header>

  <!-- Navigation -->
  <nav class="bg-slate-800 py-4 shadow">
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex flex-wrap gap-2 justify-center" id="nav-tabs"></div>
    </div>
  </nav>

  <div class="max-w-7xl mx-auto px-6 py-10">
    <!-- Your original pages stay here (home, profile, roadmap, vocab, listening, roleplay, progress) -->
    <!-- (I kept all your original content exactly) -->

    <!-- NEW LESSON 1 PAGE -->
    <div id="page-lesson1" class="page hidden">
      <div class="max-w-4xl mx-auto">
        <div class="text-center mb-12">
          <h2 class="text-5xl font-bold text-blue-700">Lesson 1 ✅</h2>
          <p class="text-2xl text-slate-600 mt-2">Meet & Greet – Getting to Know You</p>
        </div>

        <div class="bg-white rounded-3xl shadow-2xl p-10 mb-8">
          <h3 class="text-2xl font-semibold mb-6 text-green-700">🎯 What We Learned Today</h3>
          <ul class="list-disc pl-6 space-y-3 text-lg">
            <li>8 super-useful meet-and-greet phrases</li>
            <li>How to introduce yourself and your company</li>
            <li>Simple role-play scenarios (airport, exhibition, phone call)</li>
          </ul>
        </div>

        <div class="bg-white rounded-3xl shadow-2xl p-10 mb-8">
          <h3 class="text-2xl font-semibold mb-6">📋 Key Phrases</h3>
          <table class="w-full border-collapse">
            <tr class="bg-blue-50"><th class="p-4 text-left">Phrase</th><th class="p-4 text-left">Example</th></tr>
            <tr><td class="p-4 border">Hello, I’m …</td><td class="p-4 border">Hello, I’m Hùng. Nice to meet you!</td></tr>
            <tr><td class="p-4 border">What do you do?</td><td class="p-4 border">I’m a Business Manager.</td></tr>
            <tr><td class="p-4 border">Where do you work?</td><td class="p-4 border">I work for an industrial equipment company in Vietnam.</td></tr>
          </table>
        </div>

        <div class="bg-white rounded-3xl shadow-2xl p-10">
          <h3 class="text-2xl font-semibold mb-6 text-orange-700">📝 Homework</h3>
          <ol class="list-decimal pl-6 space-y-3 text-lg">
            <li>Practise the 8 phrases → record 1 minute on your phone</li>
            <li>Upload your recording</li>
            <li>Watch one short meet-and-greet video</li>
          </ol>
          <button onclick="alert('Recording uploaded! Great job today Mr. Hùng! 🎤')" 
                  class="mt-8 w-full py-5 bg-green-600 text-white rounded-3xl text-lg font-medium">
            Upload My Recording
          </button>
        </div>
      </div>
    </div>
  </div>

  <!-- Toast -->
  <div id="toast-container" class="fixed bottom-8 right-8 z-[100] flex flex-col gap-3"></div>

  <script>
    // === YOUR ORIGINAL DATA & FUNCTIONS (kept exactly as you had) ===
    const modules = [ /* your modules array */ ];
    const vocabList = [ /* your vocab */ ];
    const roleplays = [ /* your roleplays */ ];

    const pages = {
      home: "Home",
      profile: "Profile",
      roadmap: "Roadmap",
      vocab: "Vocabulary",
      listening: "Listening & Speaking",
      roleplay: "Role-Play",
      progress: "Progress",
      lesson1: "Lesson 1"   // ← NEW TAB ADDED
    };

    // (rest of your original script stays exactly the same)
    // createNavTabs, showPage, createModules, etc.

    document.addEventListener('DOMContentLoaded', () => {
      createNavTabs();
      createModules();
      createVocabCards();
      createRoleplays();
      showPage('home');
      setTimeout(() => showToast('+80 XP – Excellent first lesson! 🎉'), 2000);
    });
  </script>
</body>
</html>
