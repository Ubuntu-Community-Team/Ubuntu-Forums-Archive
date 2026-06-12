---
title: "Fairly urgent help needed - &quot;file system with errors&quot;!"
date: 2010-04-26
forum: General Help
---

### Post by Garnett on 2010-04-26
After a fair few months of using Ubuntu without any problems I switched on yesterday to be faced with the error message in the title.

I tried booting a Mint Gloria LiveCD to run fsck, but I'm a novice and can't get it to run from the terminal.

sudo e2fsck -y -f -v /dev/hda2

I don't know how to ascertain where my main hdd is ("dev/hda2" is what I read in another thread). My hdd is ext3 and fsck gives an error saying it can't find an ext2 file system.

Heeeeeeelp!

---

### Post by cariboo on 2010-04-26
You can't run fsck on a mounted partition. To determine what partition Mint is installed on, open a terminal and type:

```
sudo fdisk -l
```

that's a lower case L, the output should look similar to this:

```
sudo fdisk -l
[sudo] password for me: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007822e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   83  Linux
/dev/sda2            1216       19458   146524160   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066215

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406   83  Linux
/dev/sdb2            1276        1530     2048287+  82  Linux swap / Solaris
/dev/sdb3            1531        9729    65858467+  83  Linux
```

In my case I have two versions of Lucid installed, but note the * beside /dev/sda1 and dev/sdb1 that denotes which partition is bootable, if say, /dev/sda1 had a file system problem, I would boot from the Live CD, then open a terminal and type:

```
sudo fsck -y /dev/sda1
```

**Note:** I don't have any Windows partitions on this system, so you may see a reference to NTFS/HPFS, those are Windows partitions.

---

### Post by Garnett on 2010-04-27
> **cariboo907 said:**
> You can't run fsck on a mounted partition. To determine what partition Mint is installed on, open a terminal and type:

```
sudo fdisk -l
```

that's a lower case L, the output should look similar to this:

```
sudo fdisk -l
[sudo] password for me: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007822e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   83  Linux
/dev/sda2            1216       19458   146524160   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066215

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406   83  Linux
/dev/sdb2            1276        1530     2048287+  82  Linux swap / Solaris
/dev/sdb3            1531        9729    65858467+  83  Linux
```

In my case I have two versions of Lucid installed, but note the * beside /dev/sda1 and dev/sdb1 that denotes which partition is bootable, if say, /dev/sda1 had a file system problem, I would boot from the Live CD, then open a terminal and type:

```
sudo fsck -y /dev/sda1
```

**Note:** I don't have any Windows partitions on this system, so you may see a reference to NTFS/HPFS, those are Windows partitions.

Dude, thanks so much. That worked a dream.

---

