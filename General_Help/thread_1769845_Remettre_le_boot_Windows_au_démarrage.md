---
title: "Remettre le boot Windows au démarrage"
date: 2011-05-28
forum: General Help
---

### Post by Xylomide on 2011-05-28
J'ai suivi un tuto qui m'a dit de mettre dans le terminale "reboot umount / virsto" et cela a redémarré mon pc. Suite à ce redémarrage, je n'ai pas compris ce qui s'est passé, mais Windows ne démarre plus, mon ordinateur affiche juste l'étape du choix pour aller dans le bios ou changer l'ordre des boot. Du coup, je n'ai plus qu'accès à Ubuntu via ma clé. Si je laisse continuer la mise en marche du pc, il me dit qu'il y a un problème lors du boot à cause d'une modification. J'aimerai savoir si vous pouviez m'aider merci. Si vous aviez un moyen de reactiver le boot windows via le terminale linux.

ps : J'ai Ubuntu sur ma clé usb et Windows (vista) en temps que système d'exploitation générale de mon pc. (je n'ai pas de port cd)

---

### Post by ram0042 on 2011-05-28
> **Xylomide said:**
> J'ai suivi un tuto qui m'a dit de mettre dans le terminale "reboot umount / virsto" et cela a redémarré mon pc. Suite à ce redémarrage, je n'ai pas compris ce qui s'est passé, mais Windows ne démarre plus, mon ordinateur affiche juste l'étape du choix pour aller dans le bios ou changer l'ordre des boot. Du coup, je n'ai plus qu'accès à Ubuntu via ma clé. Si je laisse continuer la mise en marche du pc, il me dit qu'il y a un problème lors du boot à cause d'une modification. J'aimerai savoir si vous pouviez m'aider merci. Si vous aviez un moyen de reactiver le boot windows via le terminale linux.

ps : J'ai Ubuntu sur ma clé usb et Windows (vista) en temps que système d'exploitation générale de mon pc. (je n'ai pas de port cd)
La seule façon d'obtenir Windows Vista fonctionne à nouveau est d'utiliser la commande fixmbr avec Vista recover disque ou de la partition.

---

### Post by Xylomide on 2011-05-28
Le problème c'est que Je n'ai que la page du bios/choix du boot. Je n'ai pas accès à un recovery pour réparer le Windows Vista :( et je n'ai pas de port CD pour le recover disque

---

### Post by ram0042 on 2011-05-28
> **Xylomide said:**
> Le problème c'est que Je n'ai que la page du bios/choix du boot. Je n'ai pas accès à un recovery pour réparer le Windows Vista :( et je n'ai pas de port CD pour le recover disque
Vous avez une partition de récupération ?

---

### Post by Xylomide on 2011-05-28
Non plus, enfin je ne crois pas (je ne sais pas ce que c'est)

ps : dsl je suis débutant :/

---

### Post by ram0042 on 2011-05-28
> **Xylomide said:**
> Non plus, enfin je ne crois pas (je ne sais pas ce que c'est)

ps : dsl je suis débutant :/
démarrer à partir de la clé usb et charger ubuntu
Ensuite, allez à terminal et type
```
sudo apt-get install ms-sys
```
et puis tapez
```
fdisk -l
```

puis trouver celle qui est Windows.
```
sudo ms-sys -m /dev/sda
```
où **sda** est le disque que Windows est sur

---

### Post by lisati on 2011-05-28
Translation of original post, courtesy of [Google Translation]("http://translate.google.com"), for the benefit of people who don't understand French:

> I followed a tutorial that told me to put in the terminal "reboot umount / virsto" and it restarted my pc. Following the restart, I did not understand what happened, but Windows will not boot, my computer just displays the step of choosing to go into the bios or change the order of the boot. So, I have Ubuntu via VAC has my key. If I let go the start of the pc it tells me there is a problem during the boot because of a change. I wonder if you could help me thank you. If you had a way to reactivate the windows boot linux via terminal.

ps: I have Ubuntu on my USB key and Windows (Vista)-time operating system that generally my pc. (I have no port cd)

Reminder: From the forum Code of Conduct:
> Write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries that visit here and English is the common language of these forums.

If I understand the other posts correctly, the OP is a beginner who hasn't been given a choice at boot time, and doesn't have access to a repair or recovery partition.

---

### Post by Xylomide on 2011-05-29
Terminale de Xylomide

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet ms-sys
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk*: option invalide -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$ sudo ms-sys -m/dev/sda
sudo: ms-sys: command not found
ubuntu@ubuntu:~$ 



J'ai tenté l'opération que vous m'avez conseillé, mais ça n'a pas l'air de fonctionner :s

---

