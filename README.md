##  **Exercice 2 – Manipulation avancée des conteneurs**

**Objectif :** Explorer les fonctionnalités avancées de Docker : interaction avec les conteneurs, transfert de fichiers et création d’images personnalisées.

---

### 🔹 **1. Lancer un conteneur Ubuntu en mode interactif**

```bash
docker run -it --name ubuntu-test ubuntu
```

**Commentaire :**

> `-it` permet d’ouvrir une session interactive dans le conteneur.
> `--name ubuntu-test` donne un nom facile à retenir pour le conteneur.
> `ubuntu` est l’image officielle Ubuntu.

 **Capture :** terminal montrant le shell à l’intérieur du conteneur.

<img width="1065" height="228" alt="image" src="https://github.com/user-attachments/assets/e7a8f6ca-d80b-4336-b3f6-0e0ad5cd55ed" />


### 🔹 **2. Installer curl et vim dans le conteneur**

```bash
apt update
apt install -y curl vim
```

 **Commentaire :**

> `apt update` met à jour la liste des paquets.
> `apt install -y curl vim` installe curl (outil réseau) et vim (éditeur de texte) sans demander de confirmation.

 **Capture :** installation réussie.

<img width="1547" height="216" alt="image" src="https://github.com/user-attachments/assets/f0431081-dde0-4bb1-ab69-19c4e69e4fac" />

### 🔹 **3. Créer un fichier `test.txt` avec du contenu**

```bash
echo "Ceci est un fichier de test" > test.txt
```

 **Commentaire :**

> Crée un fichier texte simple dans le conteneur.
> Tu peux vérifier son contenu avec :

```bash
cat test.txt
```

 **Capture :** terminal affichant le contenu du fichier.

<img width="957" height="45" alt="image" src="https://github.com/user-attachments/assets/c393dabb-fb60-4be8-8a1f-073e54304e47" />

### 🔹 **4. Sortir du conteneur sans l’arrêter**

 Dans CMD, appuie sur :

```
Ctrl + P puis Ctrl + Q
```

 **Commentaire :**

> Permet de détacher le conteneur tout en le laissant en cours d’exécution.



### 🔹 **5. Copier le fichier du conteneur vers la machine**

```bash
docker cp ubuntu-test:/test.txt C:\Users\Noura\Desktop\test.txt
```

 **Commentaire :**

> Copie le fichier depuis le conteneur vers ton ordinateur hôte pour pouvoir le modifier facilement.

**Capture :** le fichier apparaît sur ton bureau ou le chemin choisi.

<img width="785" height="57" alt="image" src="https://github.com/user-attachments/assets/54a6afe5-b700-479c-9f51-15c1c581e5c0" />

### 🔹 **6. Modifier le fichier sur la machine et recopier dans le conteneur**

* Modifie `test.txt` avec ton éditeur habituel (ex. Notepad ou VSCode).
* Recopie-le dans le conteneur :

```bash
docker cp C:\Users\Noura\Desktop\test.txt ubuntu-test:/test.txt
```

 **Commentaire :**

> Permet de mettre à jour le fichier dans le conteneur avec les modifications apportées sur l’hôte.

 **Capture :** terminal montrant la copie réussie.
<img width="1191" height="67" alt="image" src="https://github.com/user-attachments/assets/f7feed44-3b37-4200-b685-ae8038eb865c" />

---

### 🔹 **7. Reconnecter au conteneur et vérifier les modifications**

```bash
docker attach ubuntu-test
cat test.txt
```

 **Commentaire :**

> `attach` permet de revenir dans le conteneur en cours.
> `cat test.txt` affiche le contenu du fichier mis à jour.

 **Capture :** terminal montrant le contenu correct.

<img width="652" height="210" alt="image" src="https://github.com/user-attachments/assets/85594c7e-d0e7-446a-9aa3-485ef9e025f1" />

### 🔹 **8. Créer une nouvelle image à partir du conteneur modifié**

```bash
docker commit ubuntu-test ubuntu-custom:1.0
```

 **Commentaire :**

> `commit` crée une nouvelle image basée sur l’état actuel du conteneur.
> `ubuntu-custom:1.0` est le nom et tag de l’image.

 **Capture :** terminal confirmant la création de l’image.

<img width="903" height="92" alt="image" src="https://github.com/user-attachments/assets/b472a6c4-8fb8-4d58-8019-a9bf214d35f7" />

### 🔹 **9. Lancer un nouveau conteneur basé sur cette image**

```bash
docker run -it --name ubuntu-new ubuntu-custom:1.0
```

 **Commentaire :**

> Teste que toutes les modifications sont bien présentes dans un nouveau conteneur.


### 🔹 **10. Vérifier que les modifications sont bien présentes**

```bash
cat test.txt
```

 **Commentaire :**

> Confirme que le fichier contient bien le contenu modifié.

 **Capture :** affichage du contenu dans le terminal.

<img width="796" height="123" alt="image" src="https://github.com/user-attachments/assets/14f3ac44-b9c3-4e46-967a-bd6bed4fb7d5" />


### 🔹 **Bonus : Explorer les statistiques en temps réel**

```bash
docker stats
```

 **Commentaire :**

> Affiche l’utilisation CPU, mémoire, réseau et disque pour tous les conteneurs actifs.
> Très utile pour monitorer les performances.

 

Veux‑tu que je fasse ça ?
