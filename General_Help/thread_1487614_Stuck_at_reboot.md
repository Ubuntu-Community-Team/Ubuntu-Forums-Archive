---
title: "Stuck at reboot"
date: 2010-05-19
forum: General Help
---

### Post by UT8F on 2010-05-19
I'm using ubuntu 10.04 on Asus X50N. Everythink works perfect, except system reboot. When I tried to reboot my laptop, its stuck at  "[422.029922] reboot now" line. I must restart it with power button of my laptop. How to fix it?

---

### Post by Peter09 on 2010-05-19
Try this terminal command and see where it hangs
 
```
sudo shutdown -r now
```

---

### Post by efflandt on 2010-05-19
My old HP desktop from 2004 (which happens to have an Asus mobo) never has rebooted properly from WinXP or Linux since I installed SuSE 8.0 or 8.2 on it years ago (something apparently does not totally reset the computer properly).  And I have grub (now grub2) on a partition, not the mbr.  It seems to exit the OS but leaves the drive in a state where it is running, but not doing anything.

So when anything asks to reboot, I got in the habit of saying "later", and shutting it down completely to do a cold boot.  Although, I don't recall if I have tried a warm boot (reboot) with Ubuntu (suspend and hibernate work properly in 9.10 or 10.04).

---

