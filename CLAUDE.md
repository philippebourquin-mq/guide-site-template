# Guide Site Template

Squelette utilisé pour créer une nouvelle destination du système multi-guides. Voir [guide-engine/CLAUDE.md](https://github.com/philippebourquin-mq/guide-engine) pour l'architecture complète.

Ce repo doit être marqué **Template repository** dans ses paramètres GitHub (Settings → Template repository) pour que l'admin puisse générer de nouvelles destinations automatiquement via l'API GitHub (`.../generate`).

## Fichiers

- `index.html` — coquille statique, charge `engine.js`/`engine.css` depuis `guide-engine` et appelle `GuideEngine.init({ localStorageKey: 'guide-site-v1', dataUrl: './data.json' })`
- `data.json` — skeleton vide : `{ meta: { title, subtitle, coverImage }, sections: [] }`

## `localStorageKey` partagée entre toutes les destinations

Toutes les destinations utilisent la même valeur `'guide-site-v1'` — ce n'est **pas un bug** : localStorage est scopé par origine, et chaque destination a sa propre origine GitHub Pages (ou son propre domaine). Il n'y a donc aucun risque de collision, et pas besoin de personnaliser cette clé par destination après génération du repo.
