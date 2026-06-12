---
title: "Empathy installation breaked apt"
date: 2009-09-08
forum: General Help
---

### Post by gecka on 2009-09-08
Hello,

I have tried to install empathy on my desktop computer from ppa. It worked nicely on my laptop but on my desktop I get:

$ sudo dpkg --configure -a
Paramétrage de libempathy-gtk-common (2.26.1-1ubuntu1) ...
dpkg*: erreur de traitement de libempathy-gtk-common (--configure)*:
 le sous-processus post-installation script a retourné une erreur de sortie d'état 245
Des erreurs ont été rencontrées pendant l'exécution*:
 libempathy-gtk-common


$ sudo apt-get -f install 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 1 non mis à jour.
3 partiellement installés ou enlevés.
Après cette opération, 0o d'espace disque supplémentaires seront utilisés.
Paramétrage de libempathy-gtk-common (2.26.1-1ubuntu1) ...
dpkg*: erreur de traitement de libempathy-gtk-common (--configure)*:
 le sous-processus post-installation script a retourné une erreur de sortie d'état 245
Paramétrage de vinagre (2.27.90-0ubuntu1~ppa9.04+1) ...
dpkg*: erreur de traitement de vinagre (--configure)*:
 le sous-processus post-installation script a retourné une erreur de sortie d'état 245
Paramétrage de vino (2.27.92-0ubuntu1~ppa9.04+1) ...
dpkg*: erreur de traitement de vino (--configure)*:
 le sous-processus post-installation script a retourné une erreur de sortie d'état 245
Des erreurs ont été rencontrées pendant l'exécution*:
 libempathy-gtk-common
 vinagre
 vino
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

