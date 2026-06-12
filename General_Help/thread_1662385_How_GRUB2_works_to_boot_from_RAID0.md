---
title: "How GRUB2 works to boot from RAID0?"
date: 2011-01-08
forum: General Help
---

### Post by Zhuoxi on 2011-01-08
Hi everyone,

Last week I installed Ubuntu 10.04 i386 Desktop onto software RAID using the alternative CD.

Here is the configuration:


[LIST]
[*]/dev/md0, from /dev/sda1 and /dev/sdb1, RAID0, mounted as /boot,
[*]/dev/md1, from /dev/sda2 and /dev/sdb2, RAID0, mounted as /,
[*]/dev/md2, from /dev/sda3 and /dev/sdb3, RAID0, swap device.
[/LIST]
I install GRUB2 by default.

I'm wondering, that how and where was GRUB2 installed to boot RAID0 device? How does it work to my Ubuntu? Because even my /boot is assembled as RAID0, which means there are only halves of blocks of datum on both /dev/sda1 and /dev/sdb1, does it mean there is build-in md drive in GRUB2?

Then comes another question, If I want to install Windows 7 on the free space of one of the two hard drive, what should I do to restore the GRUB2 in order to boot both my existing Ubuntu and the Windows?

b.t.w., since I'm not native English speaker my post may appear strange. Sorry for that.

---

