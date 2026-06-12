---
title: "Synaptic Package Manager Backup"
date: 2009-08-22
forum: General Help
---

### Post by chandru155 on 2009-08-22
Hi Guys,
   I am new to Ubuntu(9.04). It has Synaptic Package Manager to download softwares. There is one option in that DOWNLOAD ONLY. If i give that option where can i find the downloaded packaged to install them offline. Also, i can make backup so that i need not download them again if i wanted to install them again. Help me with detailed instructions, I am new to Linux(Ubuntu 9.04

---

### Post by akakingess on 2009-08-22
I know all of the packages that are downloaded are saved in a particular directory for easy backup so that you don't have to download them again in order to reinstall or restore a system, but the directory is slipping my mind right now, just give me a bit tonight and I will try to find out where they are stored.

---

### Post by tgeer43 on 2009-08-22
I don't see a 'Download Only" option in Synaptic Package Manager in 9.04 64-bit but you wouldn't need to do that anyway. Unless you've configured Synaptic otherwise, its default behaviour is to save a copy of each package you install in:
```
/var/cache/apt/archives/
```When you reinstall a package with Synaptic it installs it from here if it's available.

tgeer

---

### Post by chandru155 on 2009-08-22
Thanks Guys. I use dual boot. WIndows and ubuntu. If i do anything windows, ubuntu will be damaged. So i need them when i install fresh copy of ubuntu after installing windows. Thanks.

---

### Post by akakingess on 2009-08-22
Thank you tgeer43, that was the location that was slipping through my somewhat empty head!!!

---

### Post by michy99 on 2009-08-22
If you reinstall Windows, you do not have to reinstall Ubuntu, you just have to reinstall the Grub menu.

Unless you have a Wubi install. (Reason number 4 not to use Wubi.)

---

### Post by chandru155 on 2009-08-24
I installed through through Wubi. Can i restore the Ubuntu if i format Xp

---

