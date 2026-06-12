---
title: "Wubi install faliled"
date: 2010-03-16
forum: General Help
---

### Post by naggyman on 2010-03-16
Installed wubi and after reboot the windows bootloader gives an error. I forgot the error but it doesn't want to boot into either Ubuntu or Windows, CRAP!!!!.

---

### Post by prodigy_ on 2010-03-16
If you still have your Windows installation CD (or DVD) you can boot from it and restore Windows bootloader.

HOWTOs:
[u][XP](http://www.neowin.net/forum/topic/292614-how-to-get-back-your-windows-xp-bootloader/)
[Vista/Win7](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)[/u]

---

### Post by uRock on 2010-03-16
If it is a master boot record issue. Boot the LiveCD and install Lilo using these commands ```
sudo apt-get install lilo
```
```
sudo lilo -M  /dev/sda mbr
```
This will install the Lilo boot loader and repair the MBR to boot Windows.

---

### Post by naggyman on 2010-03-16
We are just waiting for the install disk. I re read the error and it said that the install disk was needed (repear option).\\:D/

---

