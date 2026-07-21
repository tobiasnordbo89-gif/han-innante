# Han Innante – nettside

Onepager-nettside for Torolf Nordbø / Han Innante. Éi enkelt HTML-fil utan byggsteg – berre opne i nettlesaren.

---

## Kjør lokalt

### Enklaste metode (ingen installasjon)
Dobbelklikk på `index.html`. Sida opnar i nettlesaren din. Bilder og skrift lastar direkte frå same mappe.

> **Merk:** Kontaktskjemaet (Formspree) og nyheitsbrevet vil ikkje fungere lokalt – det er normalt. Dei fungerer når sida er publisert på nett.

### Med lokal webserver (tilrådast ved utvikling)
Viss du redigerer CSS/JS og vil ha automatisk oppdatering:

**Alternativ A – Python (ferdig installert på Mac):**
```bash
cd "stien/til/mappa"
python3 -m http.server 8080
```
Opne `http://localhost:8080` i nettlesaren.

**Alternativ B – VS Code Live Server:**
1. Installer utvidinga [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) i VS Code
2. Høgreklikk på `index.html` → *Open with Live Server*

---

## Publiser på GitHub Pages (gratis)

### Steg 1 – Opprett repo på GitHub
1. Gå til [github.com/new](https://github.com/new)
2. Gi repoet eit namn, t.d. `han-innante`
3. Set det til **Public**
4. Klikk *Create repository*

### Steg 2 – Last opp filene
```bash
# Første gong (initialiser git i mappa)
cd "stien/til/mappa"
git init
git add .
git commit -m "Første versjon"
git branch -M main
git remote add origin https://github.com/DITT_BRUKARNAMN/han-innante.git
git push -u origin main
```

Seinare oppdateringar:
```bash
git add .
git commit -m "Oppdaterte show-datoar"
git push
```

### Steg 3 – Slå på GitHub Pages
1. Gå til repoet på GitHub → **Settings** → **Pages**
2. Under *Source*: vel **Deploy from a branch**
3. Branch: `main` / mappe: `/ (root)`
4. Klikk *Save*

Etter 1–2 minutt er sida live på:
`https://DITT_BRUKARNAMN.github.io/han-innante/`

---

## Eige domene (valfritt)

Viss du vil ha t.d. `haninnante.no`:

1. Kjøp domenet hjå ein norsk tilbydar (f.eks. domeneshop.no, one.com)
2. I GitHub Pages-innstillingane, legg inn domenet under *Custom domain*
3. Hjå domenetilbydaren, legg til ein **CNAME**-record:
   - Name: `www`
   - Value: `DITT_BRUKARNAMN.github.io`
4. Eventuelt ein **A**-record for rot-domenet som peikar på GitHubs IP-ar:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`

---

## Rediger innhald

Alle redigerbare delar er merka med kommentarar i `index.html`. Her er dei viktigaste:

### Show-datoar
Finn `const showData = [` i `<script>`-seksjonen nedst i fila.
Legg til eller fjern objekt på dette formatet:
```js
{
  dato:    "2026-12-01",      // Format: ÅÅÅÅ-MM-DD
  tittel:  "Juleshow",
  stad:    "Stavanger konserthus",
  by:      "Stavanger",
  billett: "https://lenke.til/billettar"  // eller "" for ingen knapp
},
```
Paserte datoar vises ikkje automatisk.

### Bilete
Erstatt bildene i rotkatalogen med dine eigne.
Søk etter `BILDE:` i koden for å finne alle plassar bilder er referert.

| Fil (i dag) | Kor det brukast |
|---|---|
| `sporavaar_u_tekstKutta5mb(1).jpeg` | Hero-bakgrunn |
| `Han Innante Hero bilde.jpeg` | Om-seksjonen (karakterbilde) |
| `TorolfCcBilde.jpeg` | Pressebilder |
| `A241021HiSjFlRo5613.jpeg` | Pressebilder |
| `20130821-JLA_5744.jpg` | Pressebilder |

### Video (YouTube)
Finn `YOUTUBE_ID_HER` i HTML-en. Erstatt med ID-en frå YouTube-URL-en.
Døme: `https://youtube.com/watch?v=dQw4w9WgXcQ` → ID er `dQw4w9WgXcQ`

Fjern `<div class="video-placeholder">...</div>` og ta bort kommentarane rundt `<iframe>`-taggen.

### Kontaktskjema (Formspree)
1. Gå til [formspree.io](https://formspree.io) og opprett gratis konto
2. Opprett eit nytt skjema – du får ein kode som `xpzvqkrb`
3. Søk etter `BYTT_UT_MED_FORM_ID` i HTML-en og bytt inn koden din

### Nyheitsbrev (Mailchimp)
1. Logg inn på Mailchimp → *Audience* → *Signup forms* → *Embedded forms*
2. Kopier action-URL-en (ser ut som `https://xxx.us21.list-manage.com/subscribe/post?...`)
3. Søk etter `nbForm` i HTML-en og bytt ut `action="#"` med URL-en din

### Telefon og e-post
Søk etter `bytt ut` i HTML-en – telefon og e-post er merka der.

---

## Filstruktur

```
han-innante/
├── index.html                          ← heile sida (éi fil)
├── README.md                           ← denne fila
├── Han Innante Hero bilde.jpeg
├── TorolfCcBilde.jpeg
├── sporavaar_u_tekstKutta5mb(1).jpeg
├── A241021HiSjFlRo5613.jpeg
├── 20130821-JLA_5744.jpg
└── ... (andre biletfiler)
```

---

## Spørsmål?

Kontakt den som laga sida, eller sjå [GitHub Pages-dokumentasjonen](https://docs.github.com/en/pages).
