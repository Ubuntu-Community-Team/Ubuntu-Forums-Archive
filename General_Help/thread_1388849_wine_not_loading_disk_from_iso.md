---
title: "wine not loading disk from iso"
date: 2010-01-23
forum: General Help
---

### Post by morgonzola on 2010-01-23
hi so i want to play a game called starwars republic commando on my asus eee pc 1005ha. so i got the iso's from the phisical disks and i put them on my comp. then  i used gmount-iso to mount them to my desktop, then i used wine to install the game and this all worked. however, when i tried to run the installed game, it would tell me to please insert a disk. so i looked around and came upon some code that would help
 
$ sudo mount -o loop /home/viktor/image.iso /mnt/iso
$ cd $HOME/.wine/dosdevices
$ ln -s /mnt/iso e:
$ ln -s /home/viktor/image.iso e::

but when i run it using wine explorer, it gets past the registration page and then prompts for a disk again. is this a problem in wine config, the way i mounted it, or the actual game?

---

### Post by Mark Phelps on 2010-01-24
Are you sure that the game doesn't ALWAYS require the disk in order to run?  Some game vendors do this as a way to prevent piracy.

---

