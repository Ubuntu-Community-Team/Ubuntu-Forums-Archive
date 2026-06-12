---
title: "GRUB upgrade - lost Vista boot option"
date: 2009-11-06
forum: General Help
---

### Post by bluesuede on 2009-11-06
Hi there - hoping someone can help!

Update manager notified me of a few necessary updates this morning when I logged on - a couple of which were for GRUB. I installed and (from memory) grub-pc asked me whether to keep the current install or install the package maintainers version. I chose the package maintainer - and whether this is related or not, after the install I didn't see the normal disk listing under my places, so I rebooted and now there is no longer a Vista option.

My system has three disks - 2 x 1Tb and 1 x 500Gb. One of the 1Tb disks is in two partitions - the Vista C drive and D drive, the 500Gb disk is the Vista E drive and the other 1Tb is my ubuntu install. Default OS is ubuntu, and of course this still loads fine.

This is the output from fdsik -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabf6847b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26134   209920000    7  HPFS/NTFS
/dev/sda2           26134      121601   766838784    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006cbf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      120283   966173166   83  Linux
/dev/sdb2          120284      121601    10586835    5  Extended
/dev/sdb5          120284      121601    10586803+  82  Linux swap / Solaris

It doesn't even show my 500Gb disk at this point. If I opened up computer previously I'd see the 2 Vista disks in their three partitions listed as three separate disks with their volume labels. Now I see two disks listed as "1000 GB Hard Disk: 215 GB Filesystem" and "1000 GB Hard Disk: Data" which are just the two partitions on the one disk. Normally I'd see "Volume", "Data" and "Data" which were (approx) a 200GB disk, a 731GB disk and a 1000GB disk respectively.

I'm not sure what I need to do to fix GRUB and my system...can anyone help me out? Cheers.

---

### Post by hal10000 on 2009-11-06
> I chose the package maintainer

You better kept your own version, because the new maintainer's version of course does'nt know anything about your vista system.

To get your vista system back, we need to know what version of grub you are running
Post the output of the command:

```
grub --version
```

Also, you should post the output of ```
lspci
``` to see what happened to your third harddisk

---

### Post by bluesuede on 2009-11-06
> **hal10000 said:**
> You better kept your own version, because the new maintainer's version of course does'nt know anything about your vista system.

To get your vista system back, we need to know what version of grub you are running
Post the output of the command:

```
grub --version
```Also, you should post the output of ```
lspci
``` to see what happened to your third harddisk

It's GRUB 2, version 1.97 b4 which is the ubuntu 9.10 default. "grub --version" doesn't work

However, whilst I stupidly chose the maintainers version in the update this morning, I had previously installed Startup-Manager to see if that worked with the new GRUB version - and whilst it didn't properly, I hadn't yet removed it. I started it again and luckily it still had my Vista option listed in it, so I changed it to the default OS, closed the app, started it again, and reset it to ubuntu as default OS, closed it and rebooted. Not an elegant solution, but it restored my Vista boot option to GRUB (yay) and my disks are all visible again, and Vista boots.

I'd still like to know what I could have done manually via command line to restore it as I prefer that option.

---

### Post by hal10000 on 2009-11-06
I have not much experience with the new grub2 versio, but i guess you can find some info here: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by bluesuede on 2009-11-20
Well I booted up today and have lost the Vista boot option again and am missing a disk. Is there any way to have Grub2 reset itself/rescan disks or operating systems?

---

