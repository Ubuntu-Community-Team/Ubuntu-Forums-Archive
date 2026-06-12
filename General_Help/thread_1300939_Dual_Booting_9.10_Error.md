---
title: "Dual Booting 9.10 Error"
date: 2009-10-25
forum: General Help
---

### Post by Kilroth on 2009-10-25
Ok I have 2 hard drives. 500GB with Ubuntu 9.10
and a 80GB drive with windows Vista 
I typed in to terminal

 sudo grub-mkconfig -o /boot/grub/grub.cfg 

and I got this msg. 

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1. Check your device.map.

Well it worked but when I try to boot into windows it says Error and sends me back to where I choose the OS how do I fix this problem

---

