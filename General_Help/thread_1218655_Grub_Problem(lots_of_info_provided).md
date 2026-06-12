---
title: "Grub Problem(lots of info provided)"
date: 2009-07-20
forum: General Help
---

### Post by DamienEros on 2009-07-20
Hello Everyone. I am currently having another issue I need help with. All has been well for a while I have been duel booting with windows and Ubuntu and its been great.

Heres where things messed up. I decided to install on a usb for my friend can use Ubuntu at her own computer. 
So I installed on the usb using the "use entire disk" so the usb she has now runs Ubuntu!

The problem is her usb only works when my hard drive boots and my info only boots when her 8g is in.

I believe my hard drive no redirects to her grub menu instead of my own. How would I proceed to revert these changes?

Also how would I proceed to let the usb boot on its own?

Heres the layout of everything. 
This is my original Grub the one just loading my ubuntu and windows

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        df207e6c-2acc-4e4f-8106-da9db8167a0f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=df207e6c-2acc-4e4f-8106-da9db8167a0f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        df207e6c-2acc-4e4f-8106-da9db8167a0f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=df207e6c-2acc-4e4f-8106-da9db8167a0f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        df207e6c-2acc-4e4f-8106-da9db8167a0f
kernel        /boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


This is the grub of the usb which is now being redirected to

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        de82a962-8f40-4dec-92be-6be8ffa3ee5a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de82a962-8f40-4dec-92be-6be8ffa3ee5a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        de82a962-8f40-4dec-92be-6be8ffa3ee5a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de82a962-8f40-4dec-92be-6be8ffa3ee5a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        de82a962-8f40-4dec-92be-6be8ffa3ee5a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=df207e6c-2acc-4e4f-8106-da9db8167a0f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=df207e6c-2acc-4e4f-8106-da9db8167a0f ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/memtest86+.bin  
savedefault
boot

Partitions and hard drives are as follows

sdb1=windows
sdb4 Linux extended
sdb5 Linux ext3
sdb6 Linux Swap
Thats basicilly where my own operating systems are stored

sda1 Empty hard drive but it boots from here so basicilly if i dont have this hard drive in or as default the grub menu wont boot only windows will asuming i make the other drive default. 

sdd1 Linux ext3
sdd2 Linux extended
sdd5 linux swap
This is the usb drive. this grub menu is currently being the one loaded

---

### Post by merlinus on 2009-07-21
You might try reinstalling grub.  Boot from the live cd, and enter in a terminal:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd1,2)
root (hd1,2) #use the numbers from the previous command
setup (hd1)  #use the hdd you are booting from
quit 
```

---

### Post by philcamlin on 2009-07-21
reinstalling grub will most liekly do the trick

---

### Post by DamienEros on 2009-07-21
Reinstalling grub worked for me for restoring my info problem one solved. Didnt use the live cd to do it tho for my case I had to  type  grub> root (hd1,4> set up (hd0)  What about setting up the usb for my friend?   I'm gonna attempt to write a seperate mbr on the usb stick for now to see how that works

---

