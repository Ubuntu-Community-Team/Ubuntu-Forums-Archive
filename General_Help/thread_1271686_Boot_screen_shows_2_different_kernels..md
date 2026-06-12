---
title: "Boot screen shows 2 different kernels."
date: 2009-09-21
forum: General Help
---

### Post by MarkStarCrashes on 2009-09-21
Howdy all, 

I installed a dual-boot of Ununtu 9.04 a few days ago and the boot screen shows 2 different Ubuntu "versions(?)" ( Ubuntu 9.04, kernel 2.6.28-15-generic and Ubuntu 9.04, kernel 2.6.28-11-generic) as well as 2 instances of Windows.

> 
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        04f083b1-ff06-43a1-92c1-abdef8dabed7
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=04f083b1-ff06-43a1-92c1-abdef8dabed7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        04f083b1-ff06-43a1-92c1-abdef8dabed7
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=04f083b1-ff06-43a1-92c1-abdef8dabed7 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        04f083b1-ff06-43a1-92c1-abdef8dabed7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=04f083b1-ff06-43a1-92c1-abdef8dabed7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        04f083b1-ff06-43a1-92c1-abdef8dabed7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=04f083b1-ff06-43a1-92c1-abdef8dabed7 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        04f083b1-ff06-43a1-92c1-abdef8dabed7
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1
Is this normal?... Bad?...

What to do? What to do? :confused:

Two days in and I am as pleased as punch, but I don't want to spend any more time configuring things if I need to reinstall or something.

Thanks.

---

### Post by fela on 2009-09-21
The reason for the 2 kernels is that Ubuntu keeps old copies of kernels when it updates, in case the new kernel is broken or something. It's completely normal (you can delete the old kernel if you really want, and you know that the new kernel works).

About the 2 windows entries - there is no problem with having two, it's just unnecessary. You might aswell delete one entry from your /boot/grub/menu.lst, it's perfectly safe.

EDIT: they seem to be on different partitions. Make sure you keep one that works.

---

### Post by Gaweph on 2009-09-21
Dont worry.

Everything is fine.

Firstly the 2 versions of linux is because you have updated.

If you look at the numbers:

kernel 2.6.28-15-generic
kernel 2.6.28-11-generic

The top one is a newer kernel.
This is so that you can go back to the old one after an update if something is broken, e.g. the new kernel stops a device from working or something (generally doesnt happen though).

Secondly I sometimes have had 2 versions of windows liek that, if you look at the partitions it is saying they are on different partitions:

rootnoverify (hd0,0)
rootnoverify (hd0,1)

I think your computer most likely has a windows recovery partition, this is probably what this is.

If you want to tidy the list up after updates or anything then you can do:

```

sudo gedit /boot/grub/menu.lst

```

Hope that clarifies things for you :)

---

### Post by MarkStarCrashes on 2009-09-21
Thanks guys, I appreciate the speedy replies.

Making the break from Windows is like giving up booze. I've got a nervous excitement in the pit of my stomach...:D

---

