---
title: "install vlc"
date: 2010-03-11
forum: General Help
---

### Post by hannounest on 2010-03-11
hi
i try to install VLC with console

but i have an error i don't know haw to fix it

*********************************************
hanen@hanen-laptop:~$ sudo apt-get install vlc
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.

Puisque vous n'avez demandé qu'une seule opération, le paquet n'est
probablement pas installable et vous devriez envoyer un rapport de bogue.
L'information suivante devrait vous aider à résoudre la situation*: 

Les paquets suivants contiennent des dépendances non satisfaites*:
  vlc: Dépend: vlc-nox (= 0.9.9a-2ubuntu1) mais ne sera pas installé
       Dépend: libc6 (>= 2.8) mais 2.8~20080505-0ubuntu9 devra être installé
       Dépend: libgtk2.0-0 (>= 2.16.0) mais 2.14.4-0ubuntu1 devra être installé
       Dépend: libqtcore4 (>= 4.5.0~+rc1) mais 4.4.3-0ubuntu1.4 devra être installé
       Dépend: libqtgui4 (>= 4.5.0~+rc1) mais 4.4.3-0ubuntu1.4 devra être installé
       Dépend: libvlccore0 (>= 0.9.1) mais ne sera pas installé
E: Paquets défectueux
*********************************************

thanks for help me

---

### Post by sxmaxchine on 2010-03-11
try installing it from the software centre

---

### Post by stoneage on 2010-03-11
It looks like a version conflict..

It is telling you vlc requires libqtcore4  4.5.0 but you are asking it to install libqtcore4  4.4.3

Did you download vlc from somewhere? It is much better to install from the supported Ubuntu repositories. Try installing through the Software Centre or Synaptic.

---

