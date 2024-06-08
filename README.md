# Projet Node.js avec Docker

Ce projet est un exemple de configuration d'une application Node.js avec Docker.

## Étapes pour Construire et Exécuter le Projet

### 1. Cloner le Dépôt

Clonez ce dépôt sur votre machine locale :

git clone https://github.com/votre-utilisateur/docker-training.git
cd docker-training

### Construction de l'Image Docker
docker build -t nom_utilisateur/docker-training:version .

### Exécution du Conteneur Docker
docker run -p 3000:3000 nom_utilisateur/docker-training:version

# Utiliser l'image officielle de Node.js version 14
FROM node:14

# Définir le répertoire de travail dans le conteneur
WORKDIR /usr/src/app

# Copier les fichiers package.json et package-lock.json dans le répertoire de travail
COPY package*.json ./

# Installer les dépendances du projet
RUN npm install

# Copier le reste des fichiers du projet dans le répertoire de travail
COPY . .

# Exposer le port sur lequel l'application va tourner
EXPOSE 3000

# Définir la commande pour lancer l'application
CMD ["node", "src/index.js"]
