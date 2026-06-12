---
title: "Ubuntu 9.10 - Graphical Grub"
date: 2009-09-29
forum: General Help
---

### Post by Quarkrad on 2009-09-29
I've seen pictures of what Ubuntu 9.10 may look like and I like the look of the graphical grub.  So I thought I would install Grub 2 on my 9.04.   Disappointingly it only gave me a texted based type Grub and is ver 1.96 rather than ver 2.0???????  I now read for Ubuntu 9.10 **GRUB 2 makes it possible to create graphical boot menus** so I'm a bit confused.  When Ubuntu 9.10 comes out end October with Grub 2 will it have a graphical menu or the 'old' texted based menu like 9.04, 8.10 etc.  Also - as it looks like with 9.10 you can create a graphical menu does anybody know if, having installed grub2 on my 9.04 installation, can I create a graphical menu?  If so how or where do I go to find out?

---

### Post by steigerjb on 2009-09-29
You have to do a fresh install of Karmic Koala:

> GRUB 2 by default

GRUB 2 is the default boot loader for new installations of Karmic, replacing the previous GRUB "Legacy" boot loader. Existing systems will not be upgraded to GRUB 2 at this time, as automatically reinstalling the boot loader is an inherently risky operation.

If you wish to upgrade your system to GRUB 2, then see the GRUB 2 testing page [https://wiki.ubuntu.com/KernelTeam/Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") for instructions. See also the upstream draft manual. [http://grub.enbug.org/Manual]("http://grub.enbug.org/Manual")

Some features are still missing relative to GRUB Legacy. Notable among these are lock/password support, an equivalent of grub-reboot, and Xen handling. 

unless you want to risk trying to upgrade to Grub 2. I wouldn't try it.

---

### Post by cariboo on 2009-09-29
The aim of Karmic is to boot as fast as possible, in most cases all you see is grub loading, and then it continues on to the desktop. You never see the grub menu.

There are several threads in [Karmic Testing & Development]("http://ubuntuforums.org/forumdisplay.php?f=359") that walk you through using Grub II and theming.

---

### Post by Quarkrad on 2009-09-29
Thanks for replies - although I am still a little confused.  I did follow **[https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)** and what I got at the end of it was a text based ver 1.96 grub - for some reason I was expecting a nice looking graphical grub. From what I have read about 9.10 I have assumed 9.10 = Grub2 = nice looking graphical grub menu.  Guess I was wrong - looks to me like 9.10 = text based grub as per all the previous versions (note I duel boot to winXP so I will have a grub screen that launches).

---

### Post by oldfred on 2009-09-29
If you want pretty over speed you can add a splash image in old grub. You probably can in new grub2 also.
Search for splash image on Herman's site on customizing grub:
[http://members.iinet.net.au/~herman546/p15.html#menu.lst](http://members.iinet.net.au/~herman546/p15.html#menu.lst)

---

### Post by Quarkrad on 2009-10-08
Nothing worked - I will wait for 9.10 and reinstall so I get grub2 as part of the package.

---

