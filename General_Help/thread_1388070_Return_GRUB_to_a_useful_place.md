---
title: "Return GRUB to a useful place?"
date: 2010-01-22
forum: General Help
---

### Post by eraevous on 2010-01-22
To start with, yes I've looked elsewhere on the forum/google/GRUB wiki, but as I'm a newbie at this stuff, I dread accidentally breaking something through my own poor interpretation of the instructions.

I dual-boot Windows-7 and Ubuntu from my hard disk. I recently installed a copy of Ubuntu on a flash drive, and this results in GRUB loading from said flash drive. This is a problem because a) it's slow and b) If I lose the drive I'm hosed and c) I'd like to be able to boot my system without having to have the flash drive plugged in.

Before coming here, I've run "sudo grub-install /dev/sda1" and "sudo grub-install /dev/sdb1" in my clueless stumbling. 

fdisk gives me this:

"Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf12585c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       17890   142161716    7  HPFS/NTFS
/dev/sda3           17891       19457    12586927+   5  Extended
/dev/sda5           17891       19385    12008556   83  Linux
/dev/sda6           19386       19457      578308+  82  Linux swap / Solaris

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf290b041

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1861    14948451    c  W95 FAT32 (LBA)
/dev/sdc2            1862        1949      706860    5  Extended
/dev/sdc5            1862        1949      706828+  82  Linux swap / Solaris

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bd0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         934     7502323+  83  Linux
/dev/sdb2             935         983      393592+   5  Extended
/dev/sdb5             935         983      393561   82  Linux swap / Solaris

Disk /dev/mmcblk0: 7950 MB, 7950303232 bytes
146 heads, 11 sectors/track, 9668 cylinders
Units = cylinders of 1606 * 512 = 822272 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               6        9669     7759872    b  W95 FAT32
"

Is there any other information I should tell you?

---

### Post by rcayea on 2010-01-22
You may want to go to Synaptic Package Manager and install grub-pc. Accept the installers way of installing (you get choices). Installing this package saved my bacon for sure. I couldn't figure out how to get my two linux hds and one windows hd to boot from one list of options. After installing the 1.97 grub, I went to Synaptic and installed grub-pc and that worked perfect. Good luck.

---

### Post by eraevous on 2010-01-22
That fixed everything, thank you!

---

### Post by ajgreeny on 2010-01-22
I know next to nothing about win7 dual boots, but generally the command you ran should work fine if you used the disk device name instead of the partition.  Try again with sudo grub-install /dev/sda and sudo grub-install /dev/sdb if you wish then try booting to either of those hard disks first and you should be good to go.

If you previously had grub on one of those hard disks it will not have been removed by the usb install, but should still be there, so one or other of them as first boot device in your BIOS should still work.

---

### Post by eraevous on 2010-01-24
Now I have another problem because of my bumbling.I go to GRUB, try to load Windows 7, and it loads GRUB. Repeat as necessary. I think I wrote GRUB to the windows 7 loader, and now I don't know how to get it back, or even how to google my problem. Every attempt to find information sends me to something about windows messing up ubuntu. Any ideas?

---

### Post by drs305 on 2010-01-24
> **eraevous said:**
> Now I have another problem because of my bumbling.I go to GRUB, try to load Windows 7, and it loads GRUB. Repeat as necessary. I think I wrote GRUB to the windows 7 loader, and now I don't know how to get it back, or even how to google my problem. Every attempt to find information sends me to something about windows messing up ubuntu. Any ideas?

Take a look at this link, it works both ways (although if you are getting a grub menu after another grub menu, it may be something else).

[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

If you still have problems, run the boot info script and post the results:
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

---

### Post by eraevous on 2010-01-24
Thank you. Following that link, restoring the Windows bootloader, and then restoring the linux loader seems to have fixed everything.

---

