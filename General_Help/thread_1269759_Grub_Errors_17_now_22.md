---
title: "Grub Errors 17 now 22"
date: 2009-09-18
forum: General Help
---

### Post by danbyars on 2009-09-18
I happily installed Ubuntu 9.04 in late July, Loving it ever since, so my problem starts with some of the apps my wife uses regularly are not so Ubuntu friendly. 
As any normal husband who wish's to not enter the dog house, as my wife's complaining grew I went about setting up the Main home desktop to duel boot, of course that wasn't enough she wanted vista to automatically boot first. Sheesh! 

So my issue's start here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

I followed this tutorial to a "T",  here's a copy of the menu.lst file it asked you to cut and paste from your ubuntu:

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD/](http://neosmart.net/wiki/display/EBCD/)

## ## End Default Options ## 
title        Ubuntu 9.04, kernel 2.6.28-15-generic 
uuid        6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc 
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic 
quiet 

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) 
uuid        6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc 
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc ro  single 
initrd        /boot/initrd.img-2.6.28-15-generic 

title        Ubuntu 9.04, kernel 2.6.28-14-generic 
uuid        6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc 
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic 
quiet 

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) 
uuid        6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc 
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc ro  single 
initrd        /boot/initrd.img-2.6.28-14-generic 

title        Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid        6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic 
quiet 

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) 
uuid        6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc ro  single 
initrd        /boot/initrd.img-2.6.28-11-generic 

title        Ubuntu 9.04, memtest86+ 
uuid        6ba9d0eb-f7b4-4c4d-8a94-bd6ebac314fc 
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
rootnoverify    (hd0,1) 
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

As I went to log into ubuntu today I first found a Grub error 17, Did some reading and the best advice I could find was to update the easyBCD 1.7 to 2.0. Did that went to reboot and Now I get a Grub error 22.

I've been digging for some help most of the day, and sadlly nothing has worked so far.


Any Suggestions?

I've read that even if i do a fresh install the problem will still persist? is this true?


The cpu boots fine into Vista, go figure.


Any help greatly appreciated.

Thanks

Dan Byars

---

