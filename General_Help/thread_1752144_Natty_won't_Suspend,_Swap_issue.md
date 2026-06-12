---
title: "Natty won't Suspend, Swap issue?"
date: 2011-05-07
forum: General Help
---

### Post by Dsmithjr on 2011-05-07
Okay, I've been looking around quite a bit and I've found some good information about this issue but I'm not sure what to do next.  My issue is that after doing a clean install of Natty, my system won't suspend.  It just goes to an black screen with a non-blinking cursor in the top corner, and I have to hard reset to get it back up.

I was checking something out in Gparted yesterday when I noticed that it wasn't recognizing my Swap partition (it had the orange triangle next to it).  I thought maybe the installer didn't format my Swap correctly (even though my system will use the Swap area), so I booted up from the live CD and re-formated the the Swap as Linux/Swap.  Everything looked good in the live CD so I booted back into my system.  Unfortunately, once I was back in my system, the Swap area was again not recognized.  This issue is similar to the issue from this old thread:

[http://ubuntuforums.org/showthread.php?t=1283702](http://ubuntuforums.org/showthread.php?t=1283702)

From reading that thread, I'm guessing that maybe my Swap partition was encrypted during my install (I selected to encrypt my /home for the first time), but I'm not sure how to fix it.

Here's my output from sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x936f585e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          61      487424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              61       66541   533998593    5  Extended
/dev/sdb5              61         559     3998720   82  Linux swap / Solaris
/dev/sdb6             559        4294    29999104   83  Linux
/dev/sdb7            4294       66541   499998720   83  Linux


Here's my /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=a650e365-e4c3-45bd-9176-28891a761d21 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=2d6e5404-ff79-4b8b-b9d9-67969e6b04ba /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=9e6c9d55-c1d6-44eb-a6ed-b0c4e7792b76 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
#UUID=f85b3954-b432-4344-a310-5fbe540bda0f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


Here's my sudo blkid

/dev/sda1: LABEL="System Reserved" UUID="3034DC6434DC2F1A" TYPE="ntfs" 
/dev/sda2: UUID="B484EA2684E9EAB6" TYPE="ntfs" 
/dev/sdb1: UUID="2d6e5404-ff79-4b8b-b9d9-67969e6b04ba" TYPE="ext4" 
/dev/sdb6: UUID="a650e365-e4c3-45bd-9176-28891a761d21" TYPE="ext4" 
/dev/sdb7: UUID="9e6c9d55-c1d6-44eb-a6ed-b0c4e7792b76" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="8b8f1764-7c00-4350-aa9a-4721b49d3377" TYPE="swap"


So my Swap is /dev/sdb5, but the UUID /dev/sdb5 is different than the UUID from the "cryptswap1" listed in blkid.

I'm at a bit of a loss on how to fix this.  I was going to try what kansasnoob suggested in the older thread, but I wanted to see if there was any newer information on this first.  Maybe I'm just way over my head here???

---

