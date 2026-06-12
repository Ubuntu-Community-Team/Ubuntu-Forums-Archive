---
title: "menu.lst change during update"
date: 2012-03-18
forum: General Help
---

### Post by rng on 2012-03-18
I updated the system recently as prompted by the 'update manager' and it included some linux-generic etc (?kernel) packages. However, during installation when it asked whether to keep local menu.lst or to change it, I opted for keeping local menu.lst.  Do I need to manually update the menu.lst now or nothing needs to be done? How can I check if latest kernel etc is installed on my system now? Thanks for your help.

---

### Post by raja.genupula on 2012-03-18
```
sudo update-grub 
```
will gives you recent/latest kernels at boot .
but menu.lst means sounds its not GRUB 2 . what Ubuntu version your using . 

well for more information on Grub you read this 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by rng on 2012-03-18
I have a multiboot system with grub legacy on mbr, with grub files on a separate partition. I have Ubuntu 10.04LTS with its grub2 bootloader on its own partition, so the grub legacy chainloads to grub2 of ubuntu partition.

---

### Post by wojox on 2012-03-18
```
sudo update-grub
```
Also updates menu.lst

---

### Post by pqwoerituytrueiwoq on 2012-03-18
> **raja.genupula said:**
> ```
sudo update-grub 
```will gives you recent/latest kernels at boot .
but menu.lst means sounds its not GRUB 2 . what Ubuntu version your using . 

well for more information on Grub you read this 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
ubuntu 11.10 can have grub legacy by default if you have updated from since before 10.04 without reinstalling
8.04 updated to 10.04 updated to 12.04 would have grub legacy by default

anyway 
sudo update-grub 
would get your menu.lst up to date
you can always make a backup of your menu.lst before updating it
cp /boot/grub/menu.lst /boot/grub/menu.lst_bak-`date`

---

### Post by rng on 2012-03-18
[FONT=monospace]I hope 'sudo update-grub' command updates the menu.lst on ubuntu partition only and not on the grub partition which is linked to mbr. [/FONT]Actually, grub2 is installed on ubuntu partition (10.04LTS) but update manager asked re updating menu.lst file rather than grub.cfg file.

---

