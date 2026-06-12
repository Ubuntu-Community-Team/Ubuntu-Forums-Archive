---
title: "Bootloader Problem"
date: 2009-06-25
forum: General Help
---

### Post by T11LMG on 2009-06-25
It seems i'm in a fix. I installed ubuntu happily on my HP dv6000, fumbled with wifi and got it working, but it seems i've erased windows vista from my mbr. is there any boot manager out there that i can re-add windows vista onto my bootloader again? much appreciated!

---

### Post by lisati on 2009-06-25
Even though it's aimed at Ubuntu's bootloader disappearing, hopefully this will help; [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Note: You'll probably want to check if Windows is still in your system somewhere.

---

### Post by loomsen on 2009-06-25
*any*

MBR=one the very first 512bytes sector of your HD.
Take any live-cd, rescue-cd, super grub or whatever, install the MBR again, and you should be fine.

sudo aptitude install mbr

And then 

man install-mbr

---

### Post by T11LMG on 2009-06-25
man, tried both methods, neither works for me, the first just doesn't, and the other i just dont understand. a little more explanation would be nice.

---

### Post by linuxspy on 2009-06-25
hi, please do provide your /boot/grub/menu.lst and screen shot from menu "System - Administration - Partition Editor".
Thx.

---

### Post by bumanie on 2009-06-25
Can you post the output of > sudo fdisk -luso that we can see how your drive is partitioned and whether vista is still there. If vista is still there, it will be a matter of fixing the vista bootloader with the vista installation disk and then reinstalling grub via the live ubuntu cd.

---

