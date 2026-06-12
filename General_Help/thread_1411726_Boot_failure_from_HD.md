---
title: "Boot failure from HD"
date: 2010-02-20
forum: General Help
---

### Post by kr0b1t on 2010-02-20
I just installed Ubuntu 9.10 ( 64 bit ) and everything and grub was working fine, but since I wasn't able to see my wireless card, and installed too Fedora 12.  After installing F12, I can boot from my hard drive.  So using a live CD, selecting the [ Boot from first hard drive ] sends me to the normal grub menu with the correct entries.  From here I'm able to boot into one or the other OS.

I reinstalled grub ( with grub-install /dev/sda ) from my ubuntu distro, but I'm still unable to boot directly through the HD.

The strange thing is that I don't think is getting to grub so going to the process to reinstall the OS does not seem to be the solution.

Any ideas?:confused:

---

### Post by alexbardasu on 2010-02-20
Have you tried reinstalling GRUB from an Ubuntu Live CD?

First, find the hard drive you want to boot from with fdisk.
```
sudo fdisk -l
```
You will get something like this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004f004e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14590   117194143+   7  HPFS/NTFS
/dev/sda2           14591       19457    39094177+   5  Extended
/dev/sda5           14591       19251    37439451   83  Linux
/dev/sda6           19252       19457     1654663+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc4827d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

```

You are interested in Disk /dev/sda or Disk /dev/sdb line (yours might look differet, something like /dev/hda).

Suppose your Ubuntu is installed on sda. Type
```
grub-install /dev/sda
```

Hope that helps!

---

### Post by kr0b1t on 2010-02-20
Yes, I done a 

```
grub-install /dev/sda
```

and still doesn't work

---

