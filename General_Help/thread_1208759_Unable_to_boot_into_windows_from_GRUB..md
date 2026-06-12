---
title: "Unable to boot into windows from GRUB."
date: 2009-07-09
forum: General Help
---

### Post by dragos240 on 2009-07-09
Hi, I am currently unable to load Windows Xp (for my mom, and others) from GRUB. Here is my GRUB code for windows:

root (hd0,1)
makeactive
chainloader +1

It's on the second partition on the first and only drive. I can't seem to find what's wrong, but when I try to load windows, it boots back into grub, and returns no errors.

---

### Post by merlinus on 2009-07-09
You might try this:

title windows
rootnoverify (hd0,1)
makeactive
chainloader +1

Also post results of

```
sudo fdisk -l
```

---

### Post by dragos240 on 2009-07-09
> **merlinus said:**
> You might try this:

title windows
rootnoverify (hd0,1)
makeactive
chainloader +1

Also post results of

```
sudo fdisk -l
```

Okay, I didn't need sudo as I was root:

```

Device       Boot   Start  End      Blocks          Id   System
/dev/sda1                 1   784     6297448+     12   Compaq diagnostics
/dev/sda2     *       785   6427   45327397+    7    HPFS/NTFS
/dev/sda3             6428 12161  46058355     83   Linux

```

---

### Post by merlinus on 2009-07-09
Did you change the windows section in menu.lst to what I suggested?

---

### Post by dragos240 on 2009-07-09
> **merlinus said:**
> Did you change the windows section in menu.lst to what I suggested?


I did indeed, same result.

---

### Post by merlinus on 2009-07-09
Post menu.lst, and can you boot into windows using the xp install cd or via some other means such as supergrub?

---

### Post by dragos240 on 2009-07-09
> **merlinus said:**
> Post menu.lst, and can you boot into windows using the xp install cd or via some other means such as supergrub?


Menu.lst
```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Windows
title Windows XP (For Mom, Rita, and Jaidin)
rootnoverify (hd0,1)
makeactive
chainloader +1

# (1) Arch Linux
title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/3d394501-8c5c-423a-afd5-14dd15dd9378 ro
initrd /boot/kernel26.img

# (2) Arch Linux
title  Arch Linux Fallback
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/3d394501-8c5c-423a-afd5-14dd15dd9378 ro
initrd /boot/kernel26-fallback.img

```

---

### Post by merlinus on 2009-07-09
Where are grub root and setup located?

---

### Post by Don1500 on 2009-07-09
Change this:
# (0) Windows
title Windows XP (For Mom, Rita, and Jaidin)
rootnoverify (hd0,1)
makeactive
chainloader +1

To THIS:
# (0) Windows
title Windows XP (For Mom, Rita, and Jaidin)
rootnoverify (hd0,0)            <<<<<<<<<<<<<<<<<<< This is the change
makeactive
chainloader +1


Probably work, but won't hurt if it don't and you can switch back easy.

---

### Post by dragos240 on 2009-07-09
> **merlinus said:**
> Where are grub root and setup located?

If you mean location, they are in /boot/grub

When I set up grub, I set root as (hd0,2) and I did setup (hd0).

---

### Post by dragos240 on 2009-07-09
> **Don1500 said:**
> Change this:
# (0) Windows
title Windows XP (For Mom, Rita, and Jaidin)
rootnoverify (hd0,1)
makeactive
chainloader +1

To THIS:
# (0) Windows
title Windows XP (For Mom, Rita, and Jaidin)
rootnoverify (hd0,0)            <<<<<<<<<<<<<<<<<<< This is the change
makeactive
chainloader +1


Probably work, but won't hurt if it don't and you can switch back easy.

the first partition is windows "recovery".

---

### Post by merlinus on 2009-07-09
Again, can you boot windows from the install cd, supergrub, or any other way?

---

### Post by dragos240 on 2009-07-09
> **merlinus said:**
> Again, can you boot windows from the install cd, supergrub, or any other way?

I will try supergrub.

---

### Post by Don1500 on 2009-07-09
> **dragos240 said:**
> the first partition is windows "recovery".


True, but it is also the location of the boot loader for windows.
Try it, can't hurt.

---

### Post by dragos240 on 2009-07-09
Nope, When I tried booting into windows from another disk (in this case, the archlinux install cd), it booted into my hard drive's grub. Same result.

---

### Post by dragos240 on 2009-07-09
> **Don1500 said:**
> True, but it is also the location of the boot loader for windows.
Try it, can't hurt.

Okay, I just tried it, It boots into the windows "recovery", all this tool "recovers" is the original state of windows, and erases everything.

---

### Post by Don1500 on 2009-07-10
Ok, it didn't work, but it did show that wherever you are going to (hd0,1) is the wrong place, unless you have a corrupted install of windows. Perhaps you should save all your windows data/programs and whatnot that you don't want to lose and reinstall windows.

---

