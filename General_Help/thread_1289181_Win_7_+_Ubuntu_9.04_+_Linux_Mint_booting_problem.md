---
title: "Win 7 + Ubuntu 9.04 + Linux Mint booting problem"
date: 2009-10-12
forum: General Help
---

### Post by osbornlei on 2009-10-12
HI

I've use Wubi to install Ubuntu 9.04 64bit under Windows 7 then did the same thing to install Linux Mint 64bit but during Windows boot process, I get to chooses between Ubuntu and Windows 7 (no Linux Mint option) but the "Ubuntu" option will not allow me to boot in to Ubuntu 9.04 but instad take me to Linux Mint. I've tried to use 
```
sudo gedit /boot/grub/menu.lst
``` and then modify the booting option but just have no idea what to putdown for "kernel" and "initrd". Help please

And the other strange thing is I've add the boot option for Linux Mint under Windows Boot Manager later on but no matter choose either Ubuntu or Linux Mint to boot they both will take me to Linux Mint no matter what and GRUB will not give me option to boot in Ubuntu.

BY THE WAY: Ubuntu and Linux Mint are in the same partition but just in different folders
```
title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic
root        ()/mint/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 loop=/mint/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode)
root        ()/mint/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 loop=/mint/disks/root.disk ro ROOTFLAGS=syncio single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria x64, memtest86+
root        ()/mint/disks
kernel        /boot/memtest86+.bin

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
chainloader    +1

```

Thanks

---

### Post by P4man on 2009-10-13
> **osbornlei said:**
> 
BY THE WAY: Ubuntu and Linux Mint are in the same partition but just in different folders

AFAIK, you can't. Perhaps its theoretically possible if mint also has a wubi install, but really, this is not what wubi was designed for. Its an ugly hack to allow one to try out ubuntu without changing partitions, but the real solution is to partition your drive and give one to each OS. IOW, do a regular install.

---

### Post by osbornlei on 2009-10-14
> **P4man said:**
> AFAIK, you can't. Perhaps its theoretically possible if mint also has a wubi install, but really, this is not what wubi was designed for. Its an ugly hack to allow one to try out ubuntu without changing partitions, but the real solution is to partition your drive and give one to each OS. IOW, do a regular install.

I did thought about doing a regular but since I'm little afraid about repartitioning my hardrive as last time I delete the partition talbe by clicking some unknow buttons.

---

### Post by praveenthivari on 2009-10-14
U can use easus partition home edition from windows 7 to decrease the space on your ntfs partitions. and then with the live cd use the space to create 2 partitions.(tip: u will be provided with 3 choices to install OS on to a partition, choose the manual one)
one for the system (ie. for root folder) ( format it in ext3 or ext4 type)
other one called swap partition which can be 2-3 GB

---

### Post by P4man on 2009-10-14
> **osbornlei said:**
> I did thought about doing a regular but since I'm little afraid about repartitioning my hardrive as last time I delete the partition talbe by clicking some unknow buttons.

Do it the easy way. Resize your windows partition from within windows. Vista can do that, so I assume 7 can too. Once you resized it, you will have unused/unpartitioned space, then boot the ubuntu cd, and install it unto the unused space. Its really hard to delete a partition that way :)

---

