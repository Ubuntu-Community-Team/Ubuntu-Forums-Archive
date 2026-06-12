---
title: "The enclosing drive for the volume is locked"
date: 2009-12-01
forum: General Help
---

### Post by prions on 2009-12-01
This happens when I start up gparted. The full message is:

Failure to mount "67g volume"
The enclosing drive for the volume is locked

I'm not really sure what to do here. I've looked around the internet, but I havent been given a clear answer yet, as most of the times this happens is when someone tries to create a live usb.

---

### Post by prions on 2009-12-01
Maybe its a permissions error? Gparted doesn't display any other errors other than it's unable to mount.

Heres my fdisk -l output: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8200    65860840    7  HPFS/NTFS
/dev/sda2            9348        9729     3068415   82  Linux swap / Solaris
/dev/sda3            8201        9347     9213277+   5  Extended
/dev/sda5            8201        9347     9213246   83  Linux

Partition table entries are not in disk order

---

### Post by prions on 2009-12-02
Yesterday night it started working somehow.

I turn on the computer today and the problem is back again. :/

I'm clueless on what to do, I've never had this problem before.

---

### Post by santorini on 2010-01-09
i have a similar problem with gparted

i recall that there wasn't such a problem before, but now my problem is solved by installing ntfsprogs

it's weird that xubuntu 9.10 doesn't have it installed by default, and it seems to me that gparted locked ntfs partitions deliberately when it can't find the commandline programs provided by the package ntfsprogs. 

ya know, it's ntfsprogs that does the real thing, gparted is just the graphical frontend.

hope you haven't given up.

---

