---
title: "Disk Management Software Package"
date: 2009-07-14
forum: General Help
---

### Post by wmichaelb on 2009-07-14
Hi, I would like to mount a partition that isn't on my primary disk drive for backups. Nautilus won't recognize that second drive. I installed the Disk Management software, but when I try to open it, I get an immediate error message that states that "There are no filesystems which you are allowed to mount or unmount. Contact your administrator." Is anyone familiar with this package? I can find no documentation on the net that describes how to use it, nor any references on this forum. Any suggestions would be welcome, and thanks.

---

### Post by michy99 on 2009-07-14
What is the output of this command?```
sudo fdisk -l
```

---

### Post by wmichaelb on 2009-07-15
michy99, thanks for your help. My output from that command is:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       12158    78124095    5  Extended
/dev/sda3           12159       60801   390724897+  83  Linux
/dev/sda5            2433       12158    78124063+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b2874

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2464    19792048+  83  Linux
/dev/sdb2            2465       19457   136496272+   5  Extended
/dev/sdb5            2465        2526      497983+  82  Linux swap / Solaris
/dev/sdb6            2527       19457   135998226   83  Linux


The partition that I want to use is sda3 with 390724897+ blocks. I also have an experimental copy of Kubuntu on this drive, and I assume that the rest of what's on
this 500 GB drive involves that install.

---

