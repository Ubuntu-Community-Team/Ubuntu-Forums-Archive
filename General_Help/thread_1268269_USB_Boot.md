---
title: "USB Boot"
date: 2009-09-16
forum: General Help
---

### Post by vijay_wai on 2009-09-16
Hello all,

I just installed 8.04.1 LTS desktop edition on my usb stick.
I believe I chose the right option in the last screen of install.
My laptop boots fine when I boot normally (without USB).
When I tried to boot from usb and none of the options work...

can you please help? I think I need to reconf grub.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdeb2b78e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1314    10553344   27  Unknown
/dev/sda2   *        1314       24322   184805376    7  HPFS/NTFS

Disk /dev/sdb: 4143 MB, 4143972352 bytes
255 heads, 63 sectors/track, 503 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         475     3815406   83  Linux
/dev/sdb2             476         503      224910    5  Extended
/dev/sdb5             476         503      224878+  82  Linux swap / Solaris

---

### Post by vijay_wai on 2009-09-16
I tried following, did not work... please someone help

sudo grub

device (hd0) /dev/sda
device (hd1) /dev/sdb
root (hd1,1)
setup (hd1)
quit

---

### Post by vijay_wai on 2009-09-22
can anyone help please?

---

### Post by P4man on 2009-09-22
> **vijay_wai said:**
> I tried following, did not work... please someone help

sudo grub

device (hd0) /dev/sda
device (hd1) /dev/sdb
**[COLOR="DarkRed"]root (hd1,1)[/COLOR]**
setup (hd1)
quit

hd1,1 would be the second partition of that USB drive. Looks like that needed to be 

hd (1,0) 

(that is first partition of second drive)

---

