---
title: "GRUB blank screen"
date: 2006-06-10
forum: General Help
---

### Post by janx on 2006-06-10
After several problems trying to upgrade from Breezy, I decided to reinstall Dapper from the alternate CD. The installation ran OK. I have the Windows multi-boot loader on the MBR, and I installed GRUB on /dev/hda1.

Now, I cannot boot into Ubuntu getting a blank screen, with 'GRUB' on the upper left and a blinking cursor! 

Trying the rescue option in the alternate CD and to reinstall GRUB does not improve anything. The file system on /dev/hda1 seems to be OK because I can see it from Windows with an ext3 driver.

---

### Post by janx on 2006-06-10
Fixed. I forgot to copy the new boot image to Windows. The solution is here:
[http://ubuntuforums.org/showthread.php?t=185530&highlight=grub](http://ubuntuforums.org/showthread.php?t=185530&highlight=grub)

---

