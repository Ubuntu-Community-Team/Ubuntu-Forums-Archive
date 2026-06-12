---
title: "Installing on RAID"
date: 2010-04-07
forum: General Help
---

### Post by daz4126 on 2010-04-07
Hi,

I've just bought a new Asrock ion330 system with a RAID 1 setup. Unfortuantely I can't get Ubuntu to install on it (I'm using the latest beta of 10.4).

I can get into the Live session and the Disk Utility program whows that there are 2x250GB Hard Drives sda and sdb. I am unable to access these drives though. If I try formatting either of them I get the following error message:
An error occured while performing an operation on "250 GB Unrecognized" (Partition 1 of ATA SAMSUNG HM250HI): The daemon is being inhibited

There is also another 250GB drive shown under 'Peripheral Devices". It will let me format and mount this drive. My guess is that this is the 'drive' that the RAID setup has created as a sort of front end to the array.

But when I try to install Ubuntu, the installer only sees sda and sdb and can't get access to either of them.

Anybody know what the best thing to do is?

Cheers,

DAZ

---

### Post by daz4126 on 2010-04-07
Is it to do with this?

Installation with /boot on RAID1 fails due to a bug when installing the bootloader to disk. This bug will be addressed for 10.04 Beta 2.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/527401](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/527401)

---

### Post by gordintoronto on 2010-04-07
If it were me, I would try the latest verson of Ubuntu which has been *released*, Karmic Koala.

---

