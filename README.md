# Controverse — Site de la SAÉ 1.06

> **Faut-il autoriser les systèmes d’intelligence artificielle à produire du contenu sans supervision humaine&nbsp;?**

Site statique réalisé en HTML et CSS dans le cadre de la SAÉ 1.06 de l’IUT de Montpellier.
Il présente la controverse à travers une problématique, une analyse PESTEL, une frise
chronologique et une bibliographie commentée.

> Ce dépôt est **anonymisé** : aucune identité ni adresse e-mail n'y figure.
> Les contributions sont décrites par rôle, jamais par nom d'auteur.

- **Site en ligne&nbsp;:** espace web pédagogique de l'IUT de Montpellier
- **Dépôt GitLab&nbsp;:** espace GitLab de l'IUT de Montpellier

---

## Sommaire

1. [Équipe](#équipe)
2. [Contenu du site](#contenu-du-site)
3. [Technologies utilisées](#technologies-utilisées)
4. [Structure du projet](#structure-du-projet)
5. [Lancer le site en local](#lancer-le-site-en-local)
6. [Organisation des feuilles de style](#organisation-des-feuilles-de-style)
7. [Fonctionnalités notables](#fonctionnalités-notables)
8. [Accessibilité et bonnes pratiques](#accessibilité-et-bonnes-pratiques)
9. [Répartition du travail](#répartition-du-travail)
10. [Points connus / à faire avant publication](#points-connus--à-faire-avant-publication)

---

## Équipe

Projet réalisé par un groupe de **quatre étudiants** de la SAÉ 1.06 de l'IUT de Montpellier.

| Rôle | Contribution |
| --- | --- |
| Développeur principal | Réalisation complète du projet (HTML, CSS, hébergement) |
| Identité visuelle / intégration | Icône du site, arborescence, README, mise en évidence de la page active, intégration des liens de la bibliographie, polices d'écriture, formulaire de contact |
| Recherche et rédaction | Constitution des sources, rédaction des analyses |
| Relecture | Relecture du contenu et de la mise en forme |

## Contenu du site

| Page | Fichier | Rôle |
| --- | --- | --- |
| Accueil | `index.html` | Page de garde&nbsp;: problématique, résumé et accès aux trois pages thématiques |
| Notre controverse | `controverse.html` | Problématique, présentation, bibliographie commentée (6 sources), conclusion |
| PESTEL | `pestel.html` | Analyse en six volets&nbsp;: politique, économique, socio-culturel, technologique, écologique, légal |
| Timeline | `timeline.html` | Frise chronologique de 1950 à 2025 (11 étapes), avec sources cliquables |
| Contact | `contact.html` | Formulaire de contact (8 champs) |
| Mentions légales | `mentions-legales.html` | Mentions légales, données personnelles, cookies, accessibilité |

## Technologies utilisées

- **HTML5** — balisage sémantique (`nav`, `main`, `section`, `article`, `footer`), attributs
  `aria-*`, meta tags Open Graph.
- **CSS3** — variables CSS (`:root`), `clamp()` pour les tailles fluides, `flexbox`, media queries,
  `@font-face` avec polices auto-hébergées.
- **Aucune dépendance, aucun build, aucun JavaScript.** Les menus, le carrousel PESTEL et le
  carrousel de la timeline sont réalisés en CSS pur (cases à cocher / cases radio + `label`).

## Structure du projet

```text
sae-controverse-site/
├── index.html               # Page d'accueil
├── controverse.html          # Problématique + bibliographie commentée
├── pestel.html               # Analyse PESTEL (carrousel CSS)
├── timeline.html             # Frise chronologique
├── contact.html              # Formulaire de contact
├── mentions-legales.html     # Informations légales
├── README.md
├── .gitignore                # Fichiers d'éditeur et temporaires exclus du dépôt
├── css/
│   ├── menus.css             # Barre de navigation (commune à toutes les pages)
│   ├── main.css              # Styles partagés : polices, variables, base, pied de page
│   ├── controver.css         # Page « Notre controverse »
│   ├── pestel.css            # Page PESTEL (carrousel)
│   ├── timeline.css          # Page Timeline (frise)
│   └── formulaire.css        # Page Contact (formulaire)
├── font/
│   ├── PT_Serif/             # PT Serif (regular, italic, bold, bold italic)
│   └── Exo/                  # Exo variable (roman, italique)
└── image/
    └── favicon.png           # Icône du site (logo de navigation et favicon)
```

## Lancer le site en local

Le site est entièrement statique&nbsp;: aucun serveur n’est nécessaire. Il suffit d’ouvrir
`index.html` dans un navigateur.

```bash
# Option 1 — ouvrir directement le fichier
start index.html            # Windows
xdg-open index.html         # Linux
open index.html             # macOS

# Option 2 — servir le dossier (recommandé, pour tester comme en ligne)
python -m http.server 8000
# puis ouvrir http://localhost:8000
```

> Un simple double-clic sur `index.html` fonctionne également. Le serveur local est
> surtout utile pour tester le site dans les mêmes conditions qu’en ligne (et pour vérifier
> les chemins relatifs des ressources).

## Organisation des feuilles de style

Les feuilles sont chargées dans cet ordre sur chaque page&nbsp;:

1. `menus.css` — navigation, Hamburger, sous-menu, état actif&nbsp;;
2. `main.css` — variables (`:root`), polices, base, lien d’évitement, pied de page&nbsp;;
3. la feuille de la page (`controver.css`, `pestel.css`, `timeline.css`, `formulaire.css`).

Les couleurs et l’espacement commun sont définis une seule fois dans les variables CSS de
`main.css` (`--color-accent`, `--color-text`, `--color-border`…). Pour changer l’identité
chromatique du site, il suffit de modifier le bloc `:root`.

## Fonctionnalités notables

- **Navigation adaptative** — barre fixe en ligne triple, menu burger en dessous de 900&nbsp;px,
  sous-menu déroulant sur «&nbsp;Notre controverse&nbsp;».
- **Page active signalée** — la page courante est marquée par la classe `active` et l’attribut
  `aria-current="page"`.
- **Carrousel PESTEL** — six fiches, navigation par flèches et par points, entièrement en CSS.
- **Timeline adaptative** — alternance gauche/droite sur grand écran, colonne unique sur mobile.
- **Bibliographie cliquable** — chaque fiche source ouvre la ressource dans un nouvel onglet,
  protégé par `rel="noopener noreferrer"`.
- **Formulaire validé** — champs obligatoires, format de l’e-mail et du code postal contrôlés
  par le navigateur, attributs `autocomplete` renseignés.

## Accessibilité et bonnes pratiques

- Lien d’évitement «&nbsp;Aller au contenu principal&nbsp;» en début de page.
- Contour de focus visible sur tous les éléments interactifs (`:focus-visible`).
- Contrôles du carrousel et du menu restants focalisables au clavier.
- Titres hiérarchisés (un seul `h1` par page, `h2` pour les sous-sections) et `aria-label` sur
  les contrôles sans texte.
- Textes alternatifs ou libellés explicites pour chaque champ de formulaire.
- Typographie française&nbsp;: espaces insécables avant `?`, `:` et `!`.
- Option système «&nbsp;animations réduites&nbsp;» respectée.
- Encodage UTF-8 explicite (`<meta charset="UTF-8">`) et lien de stylesheet en chemin relatif.

## Répartition du travail

Les contributions sont listées par rôle, le dépôt étant anonymisé.

- **Développement principal** — réalisation complète de l’ensemble du projet.
- **Identité visuelle et intégration** — icône du site, gestion des répertoires, README, mise en
  évidence de la page active dans la navigation, intégration des liens dans la bibliographie
  commentée, gestion des polices d’écriture, ajout d’options et de cases à cocher dans le
  formulaire de contact, diverses modifications mineures.
- **Recherche et rédaction** — constitution des sources et rédaction des analyses.
- **Relecture** — relecture du contenu et de la mise en forme.

## Points connus / à faire avant publication

- **Formulaire de contact** — la balise `action` est **vide** (aucun point de collecte) et l’envoi se
  fait en `POST`. Avant toute mise en ligne, renseignez `action` avec une adresse gérée par l’équipe
  pédagogique&nbsp;: en l’état, les données saisies ne partent nulle part.
- **Police distante** — la page d’accueil charge «&nbsp;Limelight&nbsp;» depuis Google Fonts. Pour un
  fonctionnement 100&nbsp;% hors ligne, auto-héberger cette police dans `font/` comme les autres.
- **Suites PESTEL** — les fiches les plus longues dépassent la hauteur du cadre du carrousel&nbsp;:
  leur texte est donc rendu défilable à l’intérieur de la fiche plutôt que tronqué.