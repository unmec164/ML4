<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ML4 - Menu</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #0f0f0f 0%, #1a1a1a 100%);
      color: white;
      min-height: 100vh;
      transition: all 0.3s ease;
    }

    .navbar {
      background: linear-gradient(135deg, #00c6ff 0%, #0072ff 100%);
      padding: 15px 30px;
      box-shadow: 0 4px 20px rgba(0, 198, 255, 0.3);
      position: sticky;
      top: 0;
      z-index: 1000;
    }

    .logo a {
      color: white;
      text-decoration: none;
      font-weight: bold;
      font-size: 1.8rem;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
      transition: transform 0.3s ease;
    }

    .logo a:hover {
      transform: scale(1.05);
    }

    .main-content {
      padding: 40px 20px;
      text-align: center;
      max-width: 1200px;
      margin: 0 auto;
    }

    h1 {
      margin-bottom: 40px;
      font-size: 2.5rem;
      background: linear-gradient(135deg, #00c6ff, #0072ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      text-shadow: 0 4px 20px rgba(0, 198, 255, 0.3);
    }

    .action-buttons {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
      margin-bottom: 40px;
      padding: 0 20px;
    }

    .action-button {
      background: linear-gradient(135deg, #3b82f6, #2563eb);
      color: white;
      padding: 15px 25px;
      text-decoration: none;
      border-radius: 12px;
      font-weight: 600;
      font-size: 1rem;
      transition: all 0.3s ease;
      cursor: pointer;
      user-select: none;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
      border: none;
      position: relative;
      overflow: hidden;
    }

    .action-button::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
      transition: left 0.5s;
    }

    .action-button:hover::before {
      left: 100%;
    }

    .action-button:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 25px rgba(59, 130, 246, 0.4);
    }

    .action-button:active {
      transform: translateY(-1px);
    }

    /* Couleurs spécifiques avec gradients */
    .stream { background: linear-gradient(135deg, #1e90ff, #0066cc); }
    .game { background: linear-gradient(135deg, #32cd32, #228b22); }
    .download { background: linear-gradient(135deg, #ff4500, #cc3300); }
    .music { background: linear-gradient(135deg, #9b59b6, #7d3c98); }
    .montage { background: linear-gradient(135deg, #e67e22, #d35400); }
    .outils { background: linear-gradient(135deg, #34495e, #2c3e50); }
    .shopping { background: linear-gradient(135deg, #f39c12, #e67e22); }
    .codage { background: linear-gradient(135deg, #1abc9c, #16a085); }
    .siteweb { background: linear-gradient(135deg, #2980b9, #1f4e79); }

    /* Sections secondaires */
    .sub-options {
      display: none;
      margin-top: 30px;
      padding: 20px;
      background: rgba(255, 255, 255, 0.05);
      border-radius: 15px;
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.1);
      animation: fadeIn 0.5s ease-in-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .sub-options.active {
      display: block;
    }

    .sub-options-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 15px;
      margin-top: 20px;
    }

    .sub-options .action-button {
      margin: 0;
      padding: 12px 20px;
      font-size: 0.9rem;
      border-radius: 8px;
    }

    /* Couleurs sous-boutons avec gradients */
    .anime-sama { background: linear-gradient(135deg, #5dade2, #3498db); }
    .voiranime { background: linear-gradient(135deg, #2980b9, #1f4e79); }
    .batiav { background: linear-gradient(135deg, #95a5a6, #7f8c8d); }
    .rakuten { background: linear-gradient(135deg, #e74c3c, #c0392b); }
    .free { background: linear-gradient(135deg, #e74c3c, #c0392b); }

    .notube { background: linear-gradient(135deg, #34495e, #2c3e50); }
    .savepin { background: linear-gradient(135deg, #ff69b4, #e91e63); }
    .anyconv { background: linear-gradient(135deg, #1abc9c, #16a085); }
    .y2mate { background: linear-gradient(135deg, #e74c3c, #c0392b); }
    .onlinevideoconvert { background: linear-gradient(135deg, #3498db, #2980b9); }
    .zeemo { background: linear-gradient(135deg, #9b59b6, #8e44ad); }
    .ssstik { background: linear-gradient(135deg, #00bfff, #1e90ff); }
    .freemake { background: linear-gradient(135deg, #27ae60, #229954); }

    .spotify { background: linear-gradient(135deg, #1db954, #17a046); }
    .esound { background: linear-gradient(135deg, #8e44ad, #7d3c98); }
    .frequence { background: linear-gradient(135deg, #9b59b6, #8e44ad); }

    .canva { background: linear-gradient(135deg, #00c4cc, #00a8b0); }
    .clipchamp { background: linear-gradient(135deg, #4a90e2, #357abd); }
    .veed { background: linear-gradient(135deg, #3b5998, #2d4373); }
    .clideo { background: linear-gradient(135deg, #2ecc71, #27ae60); }
    .latte { background: linear-gradient(135deg, #f39c12, #e67e22); }
    .wondershare { background: linear-gradient(135deg, #8e44ad, #7d3c98); }
    .getyarn { background: linear-gradient(135deg, #95a5a6, #7f8c8d); }
    .adobe { background: linear-gradient(135deg, #ff0000, #cc0000); }
    .slidesgo { background: linear-gradient(135deg, #3498db, #2980b9); }

    .fotor { background: linear-gradient(135deg, #d35400, #a04000); }
    .languagetool { background: linear-gradient(135deg, #27ae60, #229954); }
    .vocalremover { background: linear-gradient(135deg, #8e44ad, #7d3c98); }
    .copilot { background: linear-gradient(135deg, #2c3e50, #1a252f); }
    .gama { background: linear-gradient(135deg, #9b59b6, #8e44ad); }
    .chatgpt { background: linear-gradient(135deg, #28a745, #1e7e34); }
    .anieraser { background: linear-gradient(135deg, #f39c12, #e67e22); }
    .scribe { background: linear-gradient(135deg, #2980b9, #1f4e79); }
    .upscale { background: linear-gradient(135deg, #000080, #000066); }
    .bandlab { background: linear-gradient(135deg, #ffc0cb, #ff91a4); }
    .heygen { background: linear-gradient(135deg, #00008b, #000066); }
    .googlefont { background: linear-gradient(135deg, #ea4335, #d33b2c); }
    .istockimage { background: linear-gradient(135deg, #f4a460, #d2691e); }
    .notrix { background: linear-gradient(135deg, #8fbc8f, #6b8e6b); }
    .flaticon { background: linear-gradient(135deg, #ff4444, #cc0000); }

    .aliexpress { background: linear-gradient(135deg, #ff6f61, #ff4444); }
    .clubic { background: linear-gradient(135deg, #34495e, #2c3e50); }
    .backmarket { background: linear-gradient(135deg, #27ae60, #229954); }
    .fakespot { background: linear-gradient(135deg, #ff8c00, #ff7700); }

    .github { background: linear-gradient(135deg, #7fffd4, #40e0d0); }
    .stackoverflow { background: linear-gradient(135deg, #ff8c00, #ff7700); }
    .codeorg { background: linear-gradient(135deg, #696969, #555555); }
    .mimo { background: linear-gradient(135deg, #4169e1, #1e3a8a); }

    .squarespace { background: linear-gradient(135deg, #40e0d0, #00ced1); }

    /* Responsive Design */
    @media (max-width: 768px) {
      .main-content {
        padding: 20px 10px;
      }

      h1 {
        font-size: 2rem;
        margin-bottom: 30px;
      }

      .action-buttons {
        grid-template-columns: 1fr;
        gap: 15px;
      }

      .sub-options-grid {
        grid-template-columns: 1fr;
      }

      .navbar {
        padding: 10px 20px;
      }

      .logo a {
        font-size: 1.5rem;
      }
    }

    /* Animations d'entrée */
    .action-button {
      animation: slideUp 0.6s ease-out forwards;
      opacity: 0;
      transform: translateY(20px);
    }

    .action-button:nth-child(1) { animation-delay: 0.1s; }
    .action-button:nth-child(2) { animation-delay: 0.2s; }
    .action-button:nth-child(3) { animation-delay: 0.3s; }
    .action-button:nth-child(4) { animation-delay: 0.4s; }
    .action-button:nth-child(5) { animation-delay: 0.5s; }
    .action-button:nth-child(6) { animation-delay: 0.6s; }
    .action-button:nth-child(7) { animation-delay: 0.7s; }
    .action-button:nth-child(8) { animation-delay: 0.8s; }
    .action-button:nth-child(9) { animation-delay: 0.9s; }

    @keyframes slideUp {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    /* Indicateur de section active */
    .action-button.active {
      transform: translateY(-3px);
      box-shadow: 0 8px 25px rgba(59, 130, 246, 0.6);
    }
  </style>
</head>
<body>
  <nav class="navbar">
    <div class="logo">
      <a href="#" onclick="location.reload()">ML4</a>
    </div>
  </nav>

  <main class="main-content">
    <h1>Bienvenue Marc Elie, que veux-tu faire ?</h1>
    
    <div class="action-buttons">
      <button id="stream-btn" class="action-button stream">
        <span>🎬</span> Streaming
      </button>
      <a href="https://www.snokido.fr/" target="_blank" class="action-button game">
        <span>🎮</span> Gaming
      </a>
      <button id="download-btn" class="action-button download">
        <span>📥</span> Téléchargeur
      </button>
      <button id="music-btn" class="action-button music">
        <span>🎶</span> Musique
      </button>
      <button id="montage-btn" class="action-button montage">
        <span>🎥</span> Montage
      </button>
      <button id="tools-btn" class="action-button outils">
        <span>🧠</span> Outils
      </button>
      <button id="shopping-btn" class="action-button shopping">
        <span>🛍️</span> Shopping
      </button>
      <button id="coding-btn" class="action-button codage">
        <span>💻</span> Codage
      </button>
      <button id="siteweb-btn" class="action-button siteweb">
        <span>🌐</span> Site Web
      </button>
    </div>

    <!-- Sections secondaires -->
    <div class="sub-options" id="stream-options">
      <h3>🎬 Plateformes de Streaming</h3>
      <div class="sub-options-grid">
        <a href="https://anime-sama.fr/" target="_blank" class="action-button anime-sama">Anime Sama</a>
        <a href="https://v6.voiranime.com/" target="_blank" class="action-button voiranime">VoirAnime</a>
        <a href="https://batiav.com/4k2qyb4h7g44/home/batiav" target="_blank" class="action-button batiav">Batiav</a>
        <a href="https://www.rakuten.tv/fr/gardens/avod" target="_blank" class="action-button rakuten">Rakuten</a>
        <a href="https://oqee.tv/home" target="_blank" class="action-button free">Free</a>
      </div>
    </div>

    <div class="sub-options" id="download-options">
      <h3>📥 Outils de Téléchargement</h3>
      <div class="sub-options-grid">
        <a href="https://notube.lol/fr/youtube-app-174" target="_blank" class="action-button notube" title="Téléchargement Youtube">Notube</a>
        <a href="https://www.savepin.app/fr/" target="_blank" class="action-button savepin" title="Pinterest">Savepin</a>
        <a href="https://anyconv.com/fr/convertisseur-de-mp4-en-amv/" target="_blank" class="action-button anyconv" title="Convertisseur MP3">AnyConv</a>
        <a href="https://www-y2mate.com/fr20/" target="_blank" class="action-button y2mate">Y2mate</a>
        <a href="https://onlinevideoconverter.to/fr11Mo/" target="_blank" class="action-button onlinevideoconvert">OnlineVideoConvert</a>
        <a href="https://zeemo.ai/fr/downloadVideo" target="_blank" class="action-button zeemo">Zeemo</a>
        <a href="https://ssstik.io/fr" target="_blank" class="action-button ssstik">SssTik</a>
        <a href="https://www.freemake.com/fr/free_video_downloader_splendid/" target="_blank" class="action-button freemake">Freemake</a>
      </div>
    </div>

    <div class="sub-options" id="music-options">
      <h3>🎶 Plateformes Musicales</h3>
      <div class="sub-options-grid">
        <a href="https://open.spotify.com/intl-fr/" target="_blank" class="action-button spotify">Spotify</a>
        <a href="https://listen.esound.app/" target="_blank" class="action-button esound">Esound</a>
        <a href="https://www.frequenceplus.fr/jeux" target="_blank" class="action-button frequence">Frequence</a>
      </div>
    </div>

    <div class="sub-options" id="montage-options">
      <h3>🎥 Outils de Montage</h3>
      <div class="sub-options-grid">
        <a href="https://www.canva.com/" target="_blank" class="action-button canva">Canva</a>
        <a href="https://app.clipchamp.com/" target="_blank" class="action-button clipchamp">ClipChamp</a>
        <a href="https://www.veed.io/" target="_blank" class="action-button veed">Veed</a>
        <a href="https://clideo.com/fr/account/projects" target="_blank" class="action-button clideo">Clideo</a>
        <a href="https://platform.latte.social/" target="_blank" class="action-button latte" title="Vidéo à partir de texte">Latte</a>
        <a href="https://www.media.io/studio/project/list/start/projects" target="_blank" class="action-button wondershare">Wondershare</a>
        <a href="https://getyarn.io/" target="_blank" class="action-button getyarn" title="Phrases de films">GetYarn</a>
        <a href="https://new.express.adobe.com/" target="_blank" class="action-button adobe">Adobe</a>
        <a href="https://slidesgo.com/ai/icebreaker-generator" target="_blank" class="action-button slidesgo">Slidesgo</a>
      </div>
    </div>

    <div class="sub-options" id="tools-options">
      <h3>🧠 Outils Utiles</h3>
      <div class="sub-options-grid">
        <a href="https://www.fotor.com/photo-editor-app/editor/ai" target="_blank" class="action-button fotor">Fotor</a>
        <a href="https://languagetool.org/editor/new?login=true" target="_blank" class="action-button languagetool">LanguageTool</a>
        <a href="https://vocalremover.org/" target="_blank" class="action-button vocalremover">VocalRemover</a>
        <a href="https://copilot.microsoft.com/" target="_blank" class="action-button copilot">Copilot</a>
        <a href="https://gamma.app/create" target="_blank" class="action-button gama">Gamma</a>
        <a href="https://chatgpt.com/" target="_blank" class="action-button chatgpt">ChatGPT</a>
        <a href="https://anieraser.media.io/app/" target="_blank" class="action-button anieraser">AniEraser</a>
        <a href="https://scribehow.com/intro" target="_blank" class="action-button scribe">Scribe</a>
        <a href="https://www.upscale.media/fr" target="_blank" class="action-button upscale">Upscale</a>
        <a href="https://www.bandlab.com/explore/hip-hop" target="_blank" class="action-button bandlab">Bandlab</a>
        <a href="https://app.heygen.com/projects" target="_blank" class="action-button heygen">Heygen</a>
        <a href="https://fonts.google.com/" target="_blank" class="action-button googlefont">Google Fonts</a>
        <a href="https://www.istockphoto.com/fr" target="_blank" class="action-button istockimage">iStockImage</a>
        <a href="https://notrix.design/fr" target="_blank" class="action-button notrix">Notrix</a>
        <a href="https://www.flaticon.com/" target="_blank" class="action-button flaticon">Flaticon</a>
      </div>
    </div>

    <div class="sub-options" id="shopping-options">
      <h3>🛍️ Sites de Shopping</h3>
      <div class="sub-options-grid">
        <a href="https://fr.aliexpress.com/" target="_blank" class="action-button aliexpress">AliExpress</a>
        <a href="https://www.clubic.com/" target="_blank" class="action-button clubic">Clubic</a>
        <a href="https://www.backmarket.fr/" target="_blank" class="action-button backmarket">BackMarket</a>
        <a href="https://www.fakespot.com/" target="_blank" class="action-button fakespot">FakeSpot</a>
      </div>
    </div>

    <div class="sub-options" id="coding-options">
      <h3>💻 Ressources de Codage</h3>
      <div class="sub-options-grid">
        <a href="https://github.com/" target="_blank" class="action-button github">GitHub</a>
        <a href="https://stackoverflow.com/" target="_blank" class="action-button stackoverflow">Stack Overflow</a>
        <a href="https://code.org/" target="_blank" class="action-button codeorg">Code.org</a>
        <a href="https://mimo.org/" target="_blank" class="action-button mimo">Mimo</a>
      </div>
    </div>

    <div class="sub-options" id="siteweb-options">
      <h3>🌐 Création de Sites Web</h3>
      <div class="sub-options-grid">
        <a href="https://squarespace.com/" target="_blank" class="action-button squarespace">Squarespace</a>
      </div>
    </div>
  </main>

  <script>
    // Gestion des sections
    const sections = {
      'stream-btn': 'stream-options',
      'download-btn': 'download-options',
      'music-btn': 'music-options',
      'montage-btn': 'montage-options',
      'tools-btn': 'tools-options',
      'shopping-btn': 'shopping-options',
      'coding-btn': 'coding-options',
      'siteweb-btn': 'siteweb-options'
    };

    // Fonction pour cacher toutes les sections
    function hideAllSections() {
      document.querySelectorAll('.sub-options').forEach(section => {
        section.classList.remove('active');
      });
      document.querySelectorAll('.action-button').forEach(btn => {
        btn.classList.remove('active');
      });
    }

    // Gestion des clics
    Object.keys(sections).forEach(btnId => {
      const button = document.getElementById(btnId);
      const section = document.getElementById(sections[btnId]);
      
      if (button && section) {
        button.addEventListener('click', (e) => {
          e.preventDefault();
          
          const isActive = section.classList.contains('active');
          
          hideAllSections();
          
          if (!isActive) {
            section.classList.add('active');
            button.classList.add('active');
          }
        });
      }
    });

    // Fermer les sections en cliquant en dehors
    document.addEventListener('click', (e) => {
      if (!e.target.closest('.action-button') && !e.target.closest('.sub-options')) {
        hideAllSections();
      }
    });

    // Animation d'entrée au chargement
    document.addEventListener('DOMContentLoaded', () => {
      const buttons = document.querySelectorAll('.action-button');
      buttons.forEach((button, index) => {
        button.style.animationDelay = `${index * 0.1}s`;
      });
    });
  </script>
</body>
</html>
