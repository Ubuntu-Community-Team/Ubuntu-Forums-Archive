---
title: "After upgrade to Ubuntu 10.04 LTS wont boot to XP from GRUB"
date: 2010-05-04
forum: General Help
---

### Post by ngcampbell on 2010-05-04
I have been running ubutu 9 and xp on dual boot with no problems. yesterday I upgraded to **Ubuntu 10.04 LTS **and now when I try to boot to xp from grub I just get ,"+alt+del to restart"
I looked at the code in grub and it has
#microsoft xp
# on /dev/sda3
insmod ntfs
setroot = '(hd0,3)
search --no - floppy --fs -uuid --set 62fc2efefc2ecbdb
drivemap -s (hd0) $ {root}
chainloader +1

If anyone could help that would be great 

Aye

Neil

---

### Post by Rodney9 on 2010-05-04
Try > sudo update-grub

---

### Post by bcbc on 2010-05-04
Did you install grub to the windows partition? [This link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") shows how to diagnose and fix if you did.

---

