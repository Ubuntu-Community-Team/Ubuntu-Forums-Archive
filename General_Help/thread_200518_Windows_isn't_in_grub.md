---
title: "Windows isn't in grub"
date: 2006-06-20
forum: General Help
---

### Post by mrlinuxpt on 2006-06-20
Hi. I have windows and ubunto installed, but in Grub 0.97 windows isn't in the boot options. Is 0.95 was. How can I put windows there again? My windows version is Windows XP Home Edition OEM on SDA1. I really need windows, help me fast!

---

### Post by Ramses de Norre on 2006-06-20
```
sudo gedit /boot/grub/menu.lst
```
and add a section like this at the end: ```
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
It's possible you need to change the (hd0,0), the first digit is on which drive windows is, seconde one which partition of that drive (most commonly 0,0 for windows)

---

### Post by AdamTheCamper on 2006-06-20
Try too look into your /boot/grub/menu.lst . There should be something like 

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

Backup your menu.lst . Then try to add something like this.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This done my instalation automaticaly, but I thing it could work.  
root(hd0,0) means that your Windows is on hda1 partition. not sure if GRUB uses
(sd0,0) for serial disks.

---

### Post by mrlinuxpt on 2006-06-20
Thnaks for the help! Now I can boot Windows (sometimes!)

---

