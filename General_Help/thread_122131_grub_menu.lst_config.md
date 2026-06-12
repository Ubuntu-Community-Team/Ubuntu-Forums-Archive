---
title: "grub menu.lst config"
date: 2006-01-26
forum: General Help
---

### Post by AvvY on 2006-01-26
I am dual booting WinXP and Ubuntu with grub, but I still use WinXP as my primary OS. What is the command I need to put into the menu.lst for WinXP to be the default OS in grub?

---

### Post by o_fortuna on 2006-01-26
[QUOTE=AvvY]I am dual booting WinXP and Ubuntu with grub, but I still use WinXP as my primary OS. What is the command I need to put into the menu.lst for WinXP to be the default OS in grub?[/QUOTE]
I think all you need to do is put Windows XP first on the list, a simple matter of copying and pasting. I think you should also put "savedefault" before "chainloader + 1", and delete "savedefault" before Ubuntu. Now Windows XP should load after the countdown, and not Ubuntu.

---

### Post by Sutekh on 2006-01-26
[QUOTE=AvvY]I am dual booting WinXP and Ubuntu with grub, but I still use WinXP as my primary OS. What is the command I need to put into the menu.lst for WinXP to be the default OS in grub?[/QUOTE]
Start counting from 0 and every time you see something like

title Ubuntu 2.6.12.10-386

count up one.

When you get to Windows, find the line (near the top) that is 

default    0

and change it to the number you counted to.

---

### Post by Sutekh on 2006-01-26
A sample menu.lst

```

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
Here you'd use

default    4

---

### Post by aysiu on 2006-01-26
Applications > Accessories > Terminal

```
sudo cp /boot/grub/menu.lst /boot/grub/menu_backup.lst
sudo gedit /boot/grub/menu.lst
```

Most likely, if you scroll down, you'll see these items (or something like it):

0 Ubuntu
1 Ubuntu recovery mode
2 Ubuntu memtest
3 other operating systems
4 Windows

If you scroll back up to the top, you'll see a line that says ```
default 0
``` That means it's booting to Ubuntu as default. If you change it to ```
default 4
``` that should make Windows the default.

Count up, though. It may be #6 instead of #4.

---

### Post by AvvY on 2006-01-26
Thanx guys, the change to "default 4" worked.

I appologise for asking silly questions - I use to know this stuff but its been a while since I used Ubuntu/Linux and I seem to have forgotten bits and pieces.

---

