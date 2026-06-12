---
title: "Uninstalling ubuntu 10.04 and grub2?"
date: 2010-09-15
forum: General Help
---

### Post by ojdon on 2010-09-15
Hi there!

I currently have a dual boot setup of ubuntu 10.04 and Windows 7 using Grub2 as my boot loader. Just wondering how I could install Ubuntu 10.04 and grub2 so that I can just directly boot into Windows 7 and recover the space used for the ubuntu partition, since I currently don't need a Linux distribution any more. 

Thanks!

---

### Post by Jazzy_Jeff on 2010-09-15
You will have to repair your master boot record. This link tells you how [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html). Once this is done you will only be able to log into Windows 7. From Windows you will have to use their partition manager to format your Linux partition to what ever you want, like NTFS or fat 32. Good luck. 

**As always make sure everything important is backed up in case something does not go right.**

---

