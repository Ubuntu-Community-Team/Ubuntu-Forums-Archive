---
title: "PC-BSD + WinXP + Ubuntu"
date: 2009-07-24
forum: General Help
---

### Post by i2yu on 2009-07-24
Hi,

I've searched a lot on google on how to start PC-BSD from grub. But the two most common suggestions don't work.

Here are my Harddisks:
[IMG]http://www.ryu.at/hddgrub.jpg[/IMG] [www.ryu.at/hddgrub.jpg]("http://www.ryu.at/hddgrub.png") [www.ryu.at/hddgrub2.jpg]("http://www.ryu.at/hddgrub2.jpg")
first HDD first partition = WinXP
second HDD first partition = Ubuntu
second HDD first partition = PC-BSD
grub is installed to (hd1)

this is my menu.lst:

```

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        12d7b46c-ab6d-4243-b1c5-7ef50d856158
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=12d7b46c-ab6d-4243-b1c5-7ef50d856158 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        12d7b46c-ab6d-4243-b1c5-7ef50d856158
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=12d7b46c-ab6d-4243-b1c5-7ef50d856158 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, memtest86+
uuid        12d7b46c-ab6d-4243-b1c5-7ef50d856158
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This was added by me on 2009-07-22
title PC-BSD 7.1 - The Free Operating System
root (hd1,b)
kernel /boot/loader
boot

```selecting WinXP gives this error:
**Error 13: Invalid or unsupported executable format  Press any key to continue...**

selecting PC-BSD gives this error:
**Error 22: No such partition  Press any key to continue**

I also tried (hd1,1,a) and (hd1,1,b) and (hd0,1,a) and (hd0,1,b) for PC-BSD. None of those work.
For WinXP I don't care so much, because I can simply use the BIOS boot menu.


I hope you can help me.


EDIT:
more info:

My mainboard is GA-965P-DS3 rev3.3
This board has 2 SATA controllers, one is from Gigabyte and supports RAID, the other is on the Southbridge, from Intel (does not support RAID).
I do not use RAID. I have told my BIOS to treat all drives as IDE (or something like that).
The HDD that holds WinXP is connected to the Gigabyte SATA controller (purple connector on the board).
The HDD that holds Ubuntu and PCBSD is connected to the Intel SATA controller (yellow connector on the board).
When I installed Windows, I noticed that when I choose RAID mode in the BIOS, SATA HDDs connected to the Intel SATA controller are not recognized. So I switched to Legacy IDE mode. In this mode I noticed that my brand new 1TB HDD is not recognized properly when connected to the Gigabyte SATA controller (only recognized 31MB, later, with help of Sea-Tools from Seagate, only 3.51GB). Here, the Intel SATA controller helped me out and properly recognized it as 931GB drive.
I am not sure if this information is relevant for my question.

---

### Post by Soul-Sing on 2009-07-24
[COLOR="Magenta"]example on sda3:
[/COLOR]
title PC-BSD
rootnoverify (hd0,2)
chainloader +1
boot

add this to the menulist.

---

### Post by i2yu on 2009-07-25
thanks for the answer.

my PC-BSD is on /dev/sdb2, so the grub entry should be (hd1,1,a), right?  (hd1,1,b) is PC-BSDs swap space, right?

---

### Post by Soul-Sing on 2009-07-25
> **i2yu said:**
> thanks for the answer.

my PC-BSD is on /dev/sdb2, so the grub entry should be (hd1,1,a), right?  (hd1,1,b) is PC-BSDs swap space, right?

Yes, I think so. But I am just not very sure, I had pc-BSD 1 time installed on my computer next to Ubuntu...(sorry)

---

