---
title: "Corsair 32Gb Fast Voyageur Won't be viewed HELP!!!"
date: 2012-09-27
forum: General Help
---

### Post by corey210 on 2012-09-27
Hey everyone! I recently tried backing up some Ubuntu files to a Flash Drive and then it ended up resulting in Chaos! I copied the files to the flash drive then suddenly the flash drive became read only. I followed instructions on another forum, on trying to re-format it. Well I reformatted it to FAT-32. However, now I am no longer able to see that portion I reformatted instead all I see is a .1Mb portion. Please help! I am using Ubuntu 12.04.

Also when I ran the sudo fdisk -l I got this as the result


Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004bec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  2913564464  1456782201   83  Linux
/dev/sda2      2913564465  2930272064     8353800    5  Extended
/dev/sda5      2913564528  2930272064     8353768+  82  Linux swap / Solaris

Disk /dev/sdb: 0 MB, 79872 bytes
1 heads, 1 sectors/track, 156 cylinders, total 156 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb01f0c8

   Device Boot      Start         End      Blocks   Id  System

sdb should be 32 gigabytes. However, its not detecting all that portion for some reason?

---

