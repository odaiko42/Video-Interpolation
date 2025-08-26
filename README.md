# Interface Graphique d'Interpolation Vidéo PNG - Version Modulaire

Cette application moderne remplace le script batch original par une interface graphique modulaire avec aide contextuelle pour créer des vidéos avec interpolation à partir d'images PNG séquentielles.

## ✨ Nouvelles Fonctionnalités

- **Architecture modulaire** : Code organisé en modules séparés
- **Aide contextuelle** : Boutons d'aide (?) et info-bulles intégrés
- **Interface graphique intuitive** avec tkinter
- **Interpolation vidéo avancée** utilisant AviSynth et SVP (SmoothVideo Project)
- **Détection automatique améliorée** des numéros d'images
- **Encodage haute qualité** avec FFmpeg et codec H.265
- **Suivi du progrès** en temps réel
- **Historique des projets** avec sauvegarde/chargement
- **Estimation de durée** automatique
- **Options de ralentissement** (2x, 4x, 8x)

## 📁 Structure Modulaire

### **Fichiers principaux :**
- `video_interpolation_app.py` - Interface graphique principale modulaire
- `launch.py` - Lanceur de l'application

### **Modules métier (`core/`) :**
- `config.py` - Gestionnaire de configuration et paramètres
- `history.py` - Gestionnaire d'historique des projets
- `image_detection.py` - Détection et analyse automatique d'images
- `video_processor.py` - Traitement vidéo et génération AVS

### **Modules d'interface (`ui/`) :**
- `help_system.py` - Système d'aide contextuelle avec info-bulles

### **Documentation :**
- `README.md` - Documentation complète
- `requirements.txt` - Dépendances (modules Python standard)

## 🎯 Système d'Aide Contextuelle

### **Boutons d'aide (?) :**
Chaque paramètre dispose d'un bouton d'aide qui ouvre une fenêtre détaillée :
- **Dossier source** : Guide sur les formats et organisation des fichiers
- **Motif fichiers** : Explication des patterns (%04d.png, etc.)
- **FPS** : Différence entre FPS source et cible
- **Encodage** : Guide CRF et presets
- **Durée** : Calcul et estimation

### **Aide générale :**
- Bouton "Aide Générale" pour un guide d'utilisation rapide
- Instructions étape par étape
- Conseils d'optimisation

## 🔧 Prérequis

### Logiciels requis :
1. **Python 3.6+** avec tkinter
2. **FFmpeg** (avec codec libx265)
3. **AviSynth+** (pour le traitement vidéo)
4. **SVP (SmoothVideo Project)** (pour l'interpolation)

### Installation des dépendances :

#### Windows avec Chocolatey :
```cmd
# Installer FFmpeg
choco install ffmpeg

# Installer AviSynth+
choco install avisynth

# Télécharger SVP depuis : https://www.svp-team.com/
```

#### Installation manuelle :
1. Télécharger FFmpeg depuis https://ffmpeg.org/
2. Télécharger AviSynth+ depuis http://avisynth.nl/
3. Télécharger SVP depuis https://www.svp-team.com/

## 🚀 Utilisation

### Lancement de l'application :
```bash
python launch.py
```

### Guide d'utilisation rapide :

1. **📁 Dossier Source** : Cliquez sur "Parcourir" pour sélectionner votre dossier d'images
2. **🔍 Détection Auto** : Cliquez sur "Détecter auto" pour analyser automatiquement
3. **⚙️ Paramètres Vidéo** : 
   - FPS source : Cadence originale (généralement 24)
   - FPS cible : Cadence après interpolation (60+ pour plus de fluidité)
   - Vitesse : Normal ou ralenti (2x, 4x, 8x)
4. **📊 Calcul Durée** : Cliquez sur "Calculer" pour estimer la durée finale
5. **🎬 Génération** : Cliquez sur "Générer Vidéo"

### Interface utilisateur détaillée :

#### **Section Historique (gauche) :**
- Liste des projets précédents
- Clic pour recharger les paramètres
- Boutons Effacer/Supprimer

#### **Section Paramètres (droite) :**
- **Dossier source** : Sélection du dossier d'images PNG
- **Motif fichiers** : Format des noms (ex: `%04d.png`)
- **Images début/fin** : Plage à traiter (détection auto disponible)
- **FPS source/cible** : Cadences avant/après interpolation
- **Options ralentissement** : Normal, 2x, 4x, 8x Slowmotion
- **Estimation durée** : Calcul automatique du temps final
- **Paramètres encodage** : CRF (qualité) et preset de vitesse
- **Fichier sortie** : Emplacement de la vidéo finale

### Formats de fichiers supportés :

#### Entrée :
- PNG (recommandé)
- JPG/JPEG
- BMP, TIFF, TGA
- Séquences d'images numérotées

#### Sortie :
- MKV (recommandé)
- MP4
- AVI

## 📖 Aide Détaillée par Paramètre

### **Dossier Source :**
- Doit contenir des images numérotées consécutivement
- Évitez les espaces dans les noms de fichiers
- Formats supportés : PNG, JPG, BMP, TIFF, TGA

### **Motif des Fichiers :**
- `%04d.png` → 0001.png, 0002.png (4 chiffres avec zéros)
- `%05d.jpg` → 00001.jpg, 00002.jpg (5 chiffres)
- `frame_%03d.png` → frame_001.png, frame_002.png

### **FPS Source vs Cible :**
- **Source** : Cadence originale de vos images
- **Cible** : Cadence après interpolation
- Plus le FPS cible est élevé = mouvement plus fluide mais fichier plus volumineux

### **Options de Ralentissement :**
- **Normal Speed** : Vitesse normale
- **2x Slowmotion** : 2 fois plus lent (double la durée)
- **4x Slowmotion** : 4 fois plus lent
- **8x Slowmotion** : 8 fois plus lent

### **Paramètres d'Encodage :**
- **CRF** : 0-17 (parfait), 18-23 (excellent), 24-28 (bon)
- **Preset** : fast (recommandé), medium, slow

## 💡 Exemples d'utilisation

### Exemple 1 : Animation 3D
```
Structure :
C:\Renders\T800_Jet_002\
├── 0001.png
├── 0002.png
└── ... (1200 images)

Configuration :
- Dossier : C:\Renders\T800_Jet_002\
- Motif : %04d.png
- Images : 1 à 1200
- FPS source : 24
- FPS cible : 60
- Vitesse : Normal Speed
```

### Exemple 2 : Ralenti Dramatique
```
Configuration :
- FPS source : 30
- FPS cible : 120
- Vitesse : 4x Slowmotion
- Résultat : Vidéo très fluide et très ralentie
```

## 🔧 Paramètres d'encodage

### CRF (Constant Rate Factor) :
- **0-17** : Qualité visuelle sans perte (fichiers volumineux)
- **18-23** : Qualité très haute (recommandé)
- **24-28** : Qualité haute
- **29-35** : Qualité moyenne
- **36+** : Qualité faible

### Presets de vitesse :
- **ultrafast** : Très rapide, qualité moindre
- **fast** : Rapide, bonne qualité (recommandé)
- **medium** : Équilibre vitesse/qualité
- **slow** : Lent, meilleure qualité
- **veryslow** : Très lent, qualité maximale

## ⚡ Fonctionnalités avancées

### **Historique des Projets :**
- Sauvegarde automatique après traitement réussi
- Rechargement facile des paramètres
- 20 projets maximum conservés

### **Estimation de Durée :**
- Calcul automatique basé sur le nombre d'images
- Prise en compte du ralentissement
- Affichage en mm:ss.ms avec détails

### **Dialogue de Fin :**
- Bouton "Ouvrir dossier" pour explorer le résultat
- Bouton "Lire vidéo" pour lancement direct
- Interface moderne avec icône de succès

### **Prévisualisation AVS :**
- Affichage du script AviSynth généré
- Vérification des paramètres avant traitement
- Utile pour le débogage

## 🛠️ Dépannage

### Erreurs courantes :

1. **"FFmpeg non trouvé"** : Vérifier le chemin dans les paramètres
2. **"Aucune image détectée"** : Vérifier le motif de fichier
3. **"Erreur AviSynth"** : S'assurer qu'AviSynth+ est installé
4. **"Erreur SVP"** : Vérifier l'installation de SmoothVideo Project

### **Aide contextuelle :**
- Cliquez sur les boutons (?) pour une aide détaillée
- Consultez l'aide générale via le bouton en haut à droite
- Tous les messages apparaissent dans la zone de journal

## 📊 Comparaison avec l'ancien système

### Avantages de la version modulaire :

| Fonctionnalité | Ancien (.bat) | Nouveau (Modulaire) |
|----------------|---------------|---------------------|
| Interface | Ligne de commande | Graphique avec aide |
| Architecture | Monolithique | Modulaire |
| Aide | Aucune | Contextuelle intégrée |
| Configuration | Manuelle | Sauvegarde/chargement |
| Détection images | Manuel | Automatique améliorée |
| Suivi progrès | Aucun | Barre temps réel |
| Historique | Aucun | 20 projets sauvegardés |
| Estimation durée | Aucune | Calcul automatique |
| Ralentissement | Aucun | 4 options intégrées |
| Post-traitement | Aucun | Ouvrir/Lire intégré |

### Migration depuis l'ancien système :
1. Lancer la nouvelle interface avec `python launch.py`
2. Sélectionner le même dossier source
3. La détection automatique configurera les paramètres
4. Utiliser l'aide contextuelle pour comprendre les nouveaux paramètres
5. Sauvegarder la configuration pour usage futur

## 🏗️ Architecture du Code

### **Séparation des responsabilités :**
- **Core** : Logique métier pure
- **UI** : Interface utilisateur et aide
- **App** : Orchestration et événements

### **Avantages de la modularité :**
- Code plus maintenable
- Tests plus faciles
- Réutilisabilité des modules
- Séparation claire des responsabilités

## 📞 Support

Pour toute question ou problème :
1. Utiliser l'aide contextuelle (boutons ?)
2. Consulter l'aide générale
3. Vérifier les logs dans l'interface
4. S'assurer que tous les prérequis sont installés

## 📄 Licence

Ce projet est sous licence libre - voir le fichier LICENSE pour plus de détails.
