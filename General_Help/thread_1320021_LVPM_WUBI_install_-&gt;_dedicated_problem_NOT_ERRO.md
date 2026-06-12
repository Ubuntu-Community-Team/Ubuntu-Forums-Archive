---
title: "LVPM WUBI install -&gt; dedicated problem NOT ERROR 17"
date: 2009-11-08
forum: General Help
---

### Post by whorobj on 2009-11-08
ok i have a copy of 9.10 installed as wubi inside windows 7. It works fine.

I created a 30gb ext3 and a swap partition and i use lvpm to migrate my files.


after it prompts for reboot, i get grub and the usual error 17 cannot mount selected partition.

I change /dev disks to (hd0,1) like i'm assuming it's supposed to be, it says starting up... I get the 9.10 white ubuntu logo, then it drops to busybox shell. 



anyone have any ideas?



here is the output of fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01460146

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15632   125560288+   7  HPFS/NTFS
/dev/sda2           15633       19304    29495340   83  Linux
/dev/sda3           19305       19457     1228972+  82  Linux swap / Solaris

```





I'm out of ideas. I'm tired of the shitty disk performance.

---

