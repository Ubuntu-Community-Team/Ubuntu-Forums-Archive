---
title: "Improper shutdown and I can not boot Ubuntu Karmic"
date: 2010-01-25
forum: General Help
---

### Post by anonymtrk on 2010-01-25
Now, this is the case:

Yesterday, i tried to boot up my laptop but the battery was uncharged and it was unable to boot ubuntu karmic 64 bit. so i tried to plug the charger as soon as possible but when i looked at the screen, there was a huge black blank screen. so i had to restart it manually by pressing the power button. Now, i can see the grub screen, i can choose one of three kernels and the Windows. But only Windows can boot but the others doesn't. And also, grub timer does not work not. It does not count down to zero and autoboot the default os. I tried to reinstall grub but everytime , i got problems. [Here]("https://wiki.ubuntu.com/Grub2") is what i tried to do. In another try [here]("http://ubuntuforums.org/showthread.php?p=8415958#post8415958"), i failed again. In chroot, i could not "apt-get install" as it said i wasn't connected to internet (but i was), and in another try, it could not find p/rmonct /mnt/etc/resolv.conf. :popcorn:

---

### Post by Lars Noodén on 2010-01-25
Use the Alternate installation cd and boot into rescue mode or use the regular CD and boot into Live CD mode.  Then you can try working a little on the bootloader.

---

