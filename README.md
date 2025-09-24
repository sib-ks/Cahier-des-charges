<!--
  Fichier: Interface_Cahier_des_Charges.html
  Description: Page web single-file pour présenter un cahier des charges.
  Contenu: interface responsive, aperçu PDF par glisser-déposer, modèle téléchargeable, et instructions Git pour publier sur GitHub.
-->
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Présentation - Cahier des charges</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#06b6d4;--muted:#94a3b8;--glass: rgba(255,255,255,0.03)}
    *{box-sizing:border-box;font-family:Inter,ui-sans-serif,system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial}
    body{margin:0;background:linear-gradient(180deg,#071024 0%, #07172b 100%);color:#e6eef6;min-height:100vh}
    .container{max-width:1100px;margin:32px auto;padding:24px}
    header{display:flex;align-items:center;justify-content:space-between;gap:16px}
    .brand{display:flex;align-items:center;gap:12px}
    .logo{width:48px;height:48px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#7c3aed);display:flex;align-items:center;justify-content:center;font-weight:700}
    nav a{color:var(--muted);text-decoration:none;margin-left:14px}
    .grid{display:grid;grid-template-columns:1fr 420px;gap:20px;margin-top:22px}
    .card{background:var(--card);padding:18px;border-radius:14px;box-shadow:0 6px 18px rgba(2,6,23,0.6);backdrop-filter: blur(6px)}
    h1{margin:0 0 8px 0;font-size:20px}
    p.lead{color:var(--muted);margin:0 0 16px 0}
    .actions{display:flex;gap:12px;margin-top:12px}
    button{background:var(--accent);border: none;color:#042b33;padding:10px 14px;border-radius:10px;font-weight:600;cursor:pointer}
    button.ghost{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--muted)}
    .dropzone{margin-top:14px;padding:18px;border-radius:10px;border:2px dashed rgba(255,255,255,0.04);min-height:160px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:12px;background:var(--glass)}
    .small{font-size:13px;color:var(--muted)}
    label.file{display:inline-block;background:rgba(255,255,255,0.03);padding:8px 10px;border-radius:8px;cursor:pointer}
    .preview{width:100%;height:600px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);overflow:hidden;margin-top:12px}
    iframe{width:100%;height:100%;border:0}
    .template{white-space:pre-wrap;background:#021024;padding:12px;border-radius:8px;color:#cfeefb;font-family:monospace;margin-top:12px;max-height:360px;overflow:auto}
    footer{margin-top:18px;color:var(--muted);font-size:13px}
    @media(max-width:980px){.grid{grid-template-columns:1fr}.preview{height:360px}}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">CD</div>
        <div>
          <div style="font-weight:700">Interface Cahier de Charges</div>
          <div class="small">Prototype de page pour présenter un cahier des charges</div>
        </div>
      </div>
      <nav>
        <a href="#">Accueil</a>
        <a href="#modele">Modèle</a>
        <a href="#apercu">Aperçu</a>
      </nav>
    </header>

    <main class="grid">
      <section class="card">
        <h1>Présentation</h1>
        <p class="lead">Cette interface permet de téléverser (glisser-déposer) un PDF contenant votre cahier des charges, de le visualiser, et de télécharger un modèle prêt à remplir. Elle convient comme page de présentation dans un dépôt GitHub Pages.</p>

        <div class="actions">
          <button id="downloadModel">Télécharger le modèle</button>
          <button class="ghost" id="copyMarkdown">Copier modèle Markdown</button>
        </div>

        <div id="dropzone" class="dropzone" aria-label="Zone de dépôt de fichier">
          <div style="text-align:center">
            <strong>Glisser-déposer votre PDF ici</strong>
            <div class="small">ou</div>
            <label class="file">Sélectionner un fichier
              <input id="fileInput" type="file" accept="application/pdf" style="display:none">
            </label>
          </div>
          <div id="dropHint" class="small">Aucun fichier chargé</div>
        </div>

        <div id="meta" class="small" style="margin-top:12px"></div>

        <section id="modele" style="margin-top:18px">
          <h2 style="margin:0 0 8px 0;font-size:16px">Modèle de cahier des charges</h2>
          <div class="template" id="template">
Titre: Titre du projet

Contexte:
- Présentation du contexte et des enjeux

Objectifs:
- Objectif 1
- Objectif 2

Périmètre:
- Ce qui est inclus
- Ce qui est exclu

Livrables:
- Livrable 1
- Livrable 2

Contraintes:
- Contraintes techniques, réglementaires, budget, planning

Critères d'acceptation:
- Définition claire des critères de validation

Planning prévisionnel:
- Dates phares et jalons

Budget estimé:
- Budget approximatif

Annexes:
- Documents complémentaires
          </div>
        </section>

      </section>

      <aside>
        <div class="card">
          <h2 style="margin-top:0">Aperçu</h2>
          <p class="small">Visualisez ici le PDF chargé. Si votre navigateur ne peut pas afficher les PDF, utilisez le bouton pour télécharger.</p>
          <div class="preview" id="preview">
            <div style="display:flex;align-items:center;justify-content:center;height:100%;color:var(--muted)">Aucun aperçu</div>
          </div>

          <div style="margin-top:12px;display:flex;gap:8px">
            <a id="downloadBtn" class="ghost" style="text-decoration:none;padding:9px 10px;border-radius:8px;display:inline-block">Télécharger PDF</a>
            <button id="openInNew" class="ghost">Ouvrir dans un nouvel onglet</button>
          </div>

          <hr style="margin:14px 0;border-color:rgba(255,255,255,0.03)">
          <div>
            <strong>Publier sur GitHub</strong>
            <div class="small" style="margin-top:8px">Commandes pratiques pour mettre ce projet sur GitHub et activer GitHub Pages :</div>
            <div class="template" style="margin-top:8px;font-size:13px">
# Commandes (terminal)
mkdir mon-projet && cd mon-projet
# copier ce fichier Interface_Cahier_des_Charges.html dans le dossier
git init
git add .
git commit -m "Ajout interface cahier des charges"
gh repo create mon-projet --public --source=. --remote=origin
# ou si pas gh: créer repo sur github.com puis
git remote add origin https://github.com/VOTRE_UTILISATEUR/mon-projet.git
git push -u origin main
# Activer GitHub Pages: Paramètres -> Pages -> Branch: main / root
            </div>
          </div>
        </div>

        <div class="card" style="margin-top:12px">
          <h3 style="margin:0 0 6px 0">Astuce</h3>
          <p class="small">Renommez le fichier en <code>index.html</code> et mettez-le à la racine du dépôt pour que GitHub Pages l'affiche automatiquement.</p>
        </div>
      </aside>
    </main>

    <footer>
      Besoin que je personnalise le texte du cahier des charges ou que je prépare le dépôt GitHub complet ? Dites-moi ce que vous voulez inclure (logo, couleurs, sections supplémentaires) — je m'en occupe.
    </footer>
  </div>

  <script>
    const dropzone = document.getElementById('dropzone');
    const fileInput = document.getElementById('fileInput');
    const dropHint = document.getElementById('dropHint');
    const preview = document.getElementById('preview');
    const downloadBtn = document.getElementById('downloadBtn');
    const openInNew = document.getElementById('openInNew');
    const template = document.getElementById('template');
    const downloadModel = document.getElementById('downloadModel');
    const copyMarkdown = document.getElementById('copyMarkdown');

    let currentFileURL = null;

    function handleFile(file){
      if(!file) return;
      if(file.type !== 'application/pdf'){
        alert('Veuillez fournir un fichier PDF.');
        return;
      }
      dropHint.textContent = file.name + ' — ' + Math.round(file.size/1024) + ' KB';
      if(currentFileURL) URL.revokeObjectURL(currentFileURL);
      currentFileURL = URL.createObjectURL(file);
      preview.innerHTML = `<iframe src="${currentFileURL}"></iframe>`;
      downloadBtn.href = currentFileURL;
      downloadBtn.download = file.name;
      openInNew.onclick = ()=> window.open(currentFileURL, '_blank');
    }

    dropzone.addEventListener('click', ()=> fileInput.click());
    fileInput.addEventListener('change', (e)=> handleFile(e.target.files[0]));

    dropzone.addEventListener('dragover', (e)=>{ e.preventDefault(); dropzone.style.borderColor = 'rgba(6,182,212,0.7)'});
    dropzone.addEventListener('dragleave', ()=>{ dropzone.style.borderColor = 'rgba(255,255,255,0.04)'});
    dropzone.addEventListener('drop', (e)=>{ e.preventDefault(); dropzone.style.borderColor = 'rgba(255,255,255,0.04)'; const f = e.dataTransfer.files[0]; handleFile(f)});

    // Téléchargement du modèle en .md
    downloadModel.addEventListener('click', ()=>{
      const blob = new Blob([template.textContent], {type:'text/markdown'});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a'); a.href = url; a.download = 'modele_cahier_des_charges.md'; a.click(); URL.revokeObjectURL(url);
    });

    copyMarkdown.addEventListener('click', async ()=>{
      try{
        await navigator.clipboard.writeText(template.textContent);
        copyMarkdown.textContent = 'Copié !';
        setTimeout(()=> copyMarkdown.textContent = 'Copier modèle Markdown', 2000);
      }catch(e){ alert('Impossible de copier automatiquement.'); }
    });

  </script>
</body>
</html>
