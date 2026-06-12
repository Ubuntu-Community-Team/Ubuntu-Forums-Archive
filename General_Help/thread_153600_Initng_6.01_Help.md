---
title: "Initng 6.01 Help"
date: 2006-04-01
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-01
I'm following the Initng Tutorial in the Ubuntu Wiki. I got it installed and all that. Now I'm at the part where it says "edit your GRUB list: sudo gedit /boot/grub/menu.lst Make a duplicate Ubuntu entry and rename its title to something like Ubuntu (InitNG). In the kernel line add init=/sbin/initng"

Where is the kernel line ? Can someone who installed it post their menu.lst so I can see where it is. I have had no problem in the past installing it.

---

### Post by xXx 0wn3d xXx on 2006-04-01
anyone know ?

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=MasterChief1234]anyone know ?[/QUOTE]
Anyone know ?

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=MasterChief1234]Anyone know ?[/QUOTE]
anyone...

---

### Post by gagatz on 2006-04-03
Here you go:


## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


title		Ubuntu (InitNG)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdd1 ro quiet splash init=/sbin/initng
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

________________________________
But in my case it loads very quick until something like a DOS environment: black screen and 640x480 resolution and the offer to type something in, but i'd rather start gnome.

---

