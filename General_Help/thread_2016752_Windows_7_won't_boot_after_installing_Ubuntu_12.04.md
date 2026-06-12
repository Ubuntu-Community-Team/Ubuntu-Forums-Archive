---
title: "Windows 7 won't boot after installing Ubuntu 12.04"
date: 2012-07-04
forum: General Help
---

### Post by Chowchilla on 2012-07-04
Hi all,

I recently installed Windows 7 and then Ubuntu 12.04 on a new drive. However when trying to boot into Win 7 for the first time after installing Ubuntu I get to the Windows loading screen before what appears to be a BSOD flashes up for less than a second and the computer then reboots. If I subsequently try to boot into Windows again I'm presented with the Windows repair/boot option screen. Choosing repair does not fix the problem. Note that I am still able to boot into Ubuntu just fine.

Having done a little reading around it seems that it may be due to GRUB having been installed incorrectly. I ran "boot info script" and got the following output:

[http://pastebin.com/CgNb179T](http://pastebin.com/CgNb179T)

My disks are partitioned as follows, with sdb the new SSD and sda a HDD:

sdb1 - Win loader ("System reserved")
sdb2 - Win 7, ntfs
sdb3 - extended
sdb5 - /boot, ext2
sdb6 - swap
sdb7 - / , ext4
sdb8 - /home, ext4

sda1 - ext4 (for media files)

---

