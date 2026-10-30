# PARFUMERIE 51 — Page réseaux sociaux + QR Code

Parcours client : **QR Code imprimé → page PARFUMERIE 51 → choix du réseau**.
Aucune technologie NFC.

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | La page web (texte, design, 4 boutons, liens officiels) |
| `logo-p51.png` | Le logo affiché en haut de la page |
| `README.md` | Ce guide |

Le script `generer_qr.py` (fourni à part) fabrique le QR Code une fois l'adresse publique connue.

## Liens intégrés (non modifiés)

- Instagram : https://www.instagram.com/parfumerie___51?obrf=dmR4ZGpmenA5eDln
- TikTok : https://www.tiktok.com/@parfumerie.51
- Facebook : https://www.facebook.com/share/19h1VFQWWt/
- WhatsApp : https://wa.me/212635702000
- Téléphone : +212 635 70 20 00

---

## Étape 1 — Mettre la page en ligne gratuitement (GitHub Pages)

GitHub Pages est gratuit, sans abonnement, sans publicité et sans date d'expiration.
L'adresse obtenue ne change pas tant que vous ne renommez pas le compte ou le dépôt.
C'est essentiel : **le QR Code imprimé dépendra de cette adresse pour toujours.**

1. Créez un compte gratuit sur https://github.com (choisissez bien le nom d'utilisateur : il apparaîtra dans l'adresse, par exemple `parfumerie51`).
2. Cliquez sur **New repository** (nouveau dépôt).
   - Nom du dépôt : `parfumerie51`
   - Visibilité : **Public** (obligatoire pour l'offre gratuite)
   - Cliquez sur **Create repository**.
3. Sur la page du dépôt, cliquez sur **uploading an existing file** (ou *Add file → Upload files*).
   Glissez `index.html` et `logo-p51.png`, puis cliquez sur **Commit changes**.
4. Allez dans **Settings → Pages**.
   - *Source* : **Deploy from a branch**
   - *Branch* : **main**, dossier **/ (root)** → **Save**.
5. Patientez 1 à 3 minutes, puis rechargez la page **Settings → Pages**.
   L'adresse publique s'affiche, de la forme :
   `https://NOM-UTILISATEUR.github.io/parfumerie51/`

> Astuce : si vous nommez le dépôt exactement `NOM-UTILISATEUR.github.io`, l'adresse devient plus courte : `https://NOM-UTILISATEUR.github.io/`.

### Vérifier avant d'aller plus loin
Ouvrez l'adresse sur votre téléphone **en 4G (Wi-Fi coupé)** et touchez les 4 boutons un par un.
Chaque bouton doit ouvrir le bon compte. Si un lien est faux, corrigez-le dans `index.html` (section « LIENS OFFICIELS »), puis renvoyez le fichier sur GitHub.

---

## Étape 2 — Créer le véritable QR Code

**Ne générez le QR Code qu'après avoir testé l'adresse définitive.**

Option A — envoyez l'adresse publique à Claude : il génère le QR (SVG + PNG haute résolution), vérifie qu'il renvoie bien l'adresse, et l'intègre dans la carte.

Option B — sur un ordinateur avec Python :

```
pip install segno opencv-python-headless
python generer_qr.py https://NOM-UTILISATEUR.github.io/parfumerie51/
```

Le script crée `qr-parfumerie51.svg` (pour l'imprimeur) et `qr-parfumerie51.png`, puis relit le PNG et s'arrête en erreur si l'adresse décodée n'est pas exactement la bonne.

Évitez les sites de « QR dynamiques » gratuits : beaucoup font passer le client par leur propre adresse et désactivent le code au bout de quelques semaines, sauf abonnement payant.

---

## Étape 3 — Tester le QR Code avec un smartphone (avant l'impression en série)

1. Imprimez **une seule carte d'essai** à la taille réelle.
2. Testez au moins avec **un iPhone et un Android** : ouvrez l'appareil photo normal (sans application), visez le QR Code à 15–25 cm.
3. Une bannière doit apparaître avec l'adresse `…github.io/parfumerie51/` : touchez-la.
4. La page PARFUMERIE 51 s'ouvre : testez les 4 boutons.
5. Refaites le test sous l'éclairage réel du magasin et, si la carte sera plastifiée, sur une carte plastifiée (les reflets gênent parfois la lecture).

Seulement après ce test : lancez l'impression de toutes les cartes.

---

## Modifier le projet plus tard

- **Changer un lien** (nouveau compte, autre numéro) : modifiez le `href` concerné dans `index.html` et renvoyez le fichier sur GitHub. **Le QR Code imprimé reste valable**, inutile de réimprimer.
- **Changer le logo** : remplacez `logo-p51.png` par votre fichier officiel, avec **le même nom**.
- **Changer les textes** : ils sont lisibles directement dans `index.html`.
- **À ne jamais faire après l'impression** : renommer le compte GitHub ou le dépôt, ou supprimer le dépôt. L'adresse changerait et toutes les cartes imprimées deviendraient inutiles.
