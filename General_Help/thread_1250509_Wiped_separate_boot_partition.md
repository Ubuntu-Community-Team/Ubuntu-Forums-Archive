---
title: "Wiped separate /boot partition"
date: 2009-08-26
forum: General Help
---

### Post by WiseGuy1020 on 2009-08-26
I was screwing around and trying to boot an external HD that had windows on it and to do so I was changing /boot/grub/menu.lst. Some change happened that made grub unable to boot. This has happened to me before so I didn't panic and booted up my live cd. I mounted my /boot partition fine and was editing menu.lst when I accidentally deleted all the data from my boot partition.


My fdisk -l is:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x924efff9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+   6  FAT16
/dev/sda2            7900       19457    92839635   83  Linux
/dev/sda3              13        6091    48829567+  83  Linux

Partition table entries are not in disk order

sda1 is my separate /boot partition
sda2 is my data partition
sda3 is a LUKS encrypted partition with an LVM that contains "/" and "swap" volumes.

I know I can mount my LVM and retrieve all my data and do a fresh install but it seemed like there had to be an easier way.

I was thinking of using the alternate install cd and reinstalling just my /boot partition. But I don't think that alone will work because grub wont know to look for LUKS /dev/mapper.

Any help would be greatly appreciated as I am borrowing a friend's laptop and he is very sensitive to other people using his computer.




p.s. I never normally use a FAT16 filesystem for my boot partition I was just clicking away and missed it on installation.

---

