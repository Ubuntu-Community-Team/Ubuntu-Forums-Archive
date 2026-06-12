---
title: "Grub Will No Longer Boot Windows 7 !"
date: 2010-04-30
forum: General Help
---

### Post by TimCereja on 2010-04-30
I had been dual-booting Ubuntu and Windows 7. Today I upgraded to Ubuntu 10.04 and now Grub still has a Windows 7 boot option, but when selected it goes to a blank screen and does not boot Windows 7 as it would before. Any ideas about how this could be fixed?

---

### Post by carl4926 on 2010-04-30
Please post result of this

Open a terminal

```
sudo fdisk -l

```

---

### Post by dino99 on 2010-04-30
sudo grub-mkconfig && update-grub

---

### Post by omalsa04 on 2010-05-11
this solution worked fine for me:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by arnoutvos on 2010-07-04
i had the same problem after upgrading to Grub 2 en this worked for me too

---

