---
title: "Can't boot ubuntu- lost data, please help!!"
date: 2010-05-24
forum: General Help
---

### Post by ninah on 2010-05-24
Hi,
   I'm new to linux so please bear with me. My laptop, running karmic koala, suddenly lost it's internet connection. I decided just to reboot, but it won't. If I go to recovery I get the following 

Alert! /dev/disk/by-uuid/ xxxxxx does not exist. Dropping to a shell


Following the advice from some other threads on here I made a liveCD 
the output from fdisk -l suggests the partition I need is on sda1 

I tried to mount my drive using

sudo mount /dev/sda1 -t tmpfs /mnt 

but nothing seems to happen. however perhaps the drive is mounted and I just don't know where to look for it??



If poss Id like to recover my old install, rather than just starting again from scratch with a new install. 


very very grateful for any help!!

Ninah

---

### Post by r_s on 2010-05-24
use testdisk to recover your partition, if you have not overwritten it.
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

---

### Post by ninah on 2010-05-24
Thanks for getting back to me so quickly, I installed a temporary ubuntu from the liveCD and can see my old partition, everything is still there- thankfully. I then ran testdisk, but now I have  the following error and can't boot into either system.

error:unknown filesystem
grub rescue

cheers, Ninah

---

### Post by alexan on 2010-05-24
Follow the steps in this guide from LiveCD:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by ninah on 2010-05-24
That's ok, i reinstalled grub and can now boot into my old partition, thanks!

---

