---
title: "kernal not displayed in menu.lst"
date: 2010-01-24
forum: General Help
---

### Post by notquitestr8t on 2010-01-24
I've updated to a higher version kernal. It shows up when I run the sudo update-grub command but it's not available when grub boots. What did I miss? I should be running 2.6.31.17 but you can see below that the highest version offered is 2.6.31-16. Also, should I update to Grub2?

Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... donegedit

# ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		cf0c5765-dea3-4be8-8303-7e18ce70b5b1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=cf0c5765-dea3-4be8-8303-7e18ce70b5b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		cf0c5765-dea3-4be8-8303-7e18ce70b5b1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=cf0c5765-dea3-4be8-8303-7e18ce70b5b1 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		cf0c5765-dea3-4be8-8303-7e18ce70b5b1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=cf0c5765-dea3-4be8-8303-7e18ce70b5b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		cf0c5765-dea3-4be8-8303-7e18ce70b5b1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=cf0c5765-dea3-4be8-8303-7e18ce70b5b1 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, memtest86+
uuid		cf0c5765-dea3-4be8-8303-7e18ce70b5b1
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST

---

