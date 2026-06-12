---
title: "Need Help - Fix Grub install location [remove other thread]"
date: 2011-01-19
forum: General Help
---

### Post by EarthBoundX5 on 2011-01-19
Ok, so the basics of my problem is that I need to relocate my Grub install location.

Background info, written out as simply as possible...
*Had Triple Boot using Windows 7 Bootmgr (Windows 7, MacOSX86, Ubuntu 10.04) using chain0 and linux.bin methods for said OSs.
*No problems for several months, then out of nowhere Ubuntu would not boot.
*Seemed like a bad sector problem, ran HDD Regenerator, which did not do anything.
*Next tried checking MBR, accidentally zeroed it (was up very late and half-asleep).
*Semi-fixed issue of zeroing by using Partition recovery software, but had to boot into Windows using a boot CD, could not boot Ubuntu and could not recover Mac partition due to being off by 1 byte.  In this process, somehow my Ubuntu partition became primary and no longer existed in the extended partition.
*Eventually I just manually changed the partition table, moving Ubuntu in the extended.
*Installed Ubuntu again on a new partition (where Mac used to be), in doing so despite telling it to install grub just to that partition, it replaced my MBR as Grub...and automatically saw my old Ubuntu install and I could finally boot to it!

Any more info can be provided.


The end result I desire is using Grub as main bootloader (I am finally done with BOOTMGR), erase new ubuntu install and use space for old ubuntu install.  Primary booting being Windows, with Ubuntu as the secondary.  If possible, room for booting MacOSX86 again, but I really dont care.

EDIT: [Solved] just did a grub-install sda and then update-grub (something I had not previously been aware of)

---

