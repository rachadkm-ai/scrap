# Scraping Annuaire FHF

Ce dossier contient tous les éléments nécessaires pour faire tourner automatiquement les scripts d'extraction sur l'annuaire de la FHF (Fédération Hospitalière de France) via GitHub Actions.

## Fichiers Inclus
- `scraper_cardio.py` : Script spécialisé pour extraire uniquement les services de cardiologie, en incluant l'information sur la présence d'un plateau de cardiologie interventionnelle / coronarographie.
- `scraper_fhf_v2.py` : Script général pour extraire l'intégralité des services de l'annuaire.
- `requirements.txt` : Liste des dépendances (Playwright, Openpyxl).
- `.github/workflows/` : Configurations pour GitHub Actions.

## Automatisation GitHub Actions
Deux automatisations sont configurées :
1. **Scraping Cardio Hebdomadaire** : Se lance tout seul tous les lundis à 1h du matin (UTC) pour la cardiologie. Les résultats seront mis à jour dans `fhf_cardiologie.xlsx`.
2. **Scraping Général (Manuel)** : Permet de lancer l'extraction de tous les services manuellement. Les résultats seront enregistrés dans `fhf_etablissements.xlsx`.

### Comment lancer manuellement ?
Dans GitHub, allez dans l'onglet **Actions**, sélectionnez le workflow désiré (ex: "Scraping FHF Cardio Hebdomadaire") et cliquez sur le bouton **Run workflow** à droite.

> **Note :** Les scripts sont configurés pour ne pas surcharger les serveurs de la FHF (pause de 1,5s entre chaque action). Une exécution complète prend environ 1h30, ce qui rentre parfaitement dans la limite gratuite de 6h par tâche de GitHub Actions.
