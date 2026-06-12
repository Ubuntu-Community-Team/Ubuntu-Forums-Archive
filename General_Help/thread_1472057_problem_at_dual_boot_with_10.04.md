---
title: "problem at dual boot with 10.04"
date: 2010-05-04
forum: General Help
---

### Post by cs.thor.ro@gmail.com on 2010-05-04
I install 10.04 dual boot with live CD after install, grub show me Ubunt...W7 after selecting W7, nothing happened, just a black screen and three letters blinking. I trie to install it by upgranding an Ubuntu 9.04(that worck fine), but after upgrade, the dual boot crash in the same way.

---

### Post by dino99 on 2010-05-04
i hope you have not installed grub2 over windoz bootloader. Grub2 might be installed on the mbr lucid partition.

if you previously was using grub1 (= grub-legacy=grub), you have to remove/purge ALL the grub packages installed, and menu.lst also, then install grub-pc and grub-common, then:

sudo grub-mkconfig && update-grub

---

### Post by cs.thor.ro@gmail.com on 2010-05-04
i instaled grub on sda mbr, w7 has sda1 and ubuntu, sda5

---

### Post by cs.thor.ro@gmail.com on 2010-05-04
and when i installed ubuntu by upgading, I keep the old good working configuration...so the problem is in this new grub2

---

### Post by bcbc on 2010-05-04
See [this link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") to meierfra's page. It shows you how to check and fix if you installed grub to the windows partition. If that's not the problem you can post back the bootinfoscript results here.

---

