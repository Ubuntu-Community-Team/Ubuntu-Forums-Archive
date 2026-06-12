---
title: "Error while mounting External Drive"
date: 2010-05-16
forum: General Help
---

### Post by optix7 on 2010-05-16
my simpledrive external drive works fine on windows but i keep getting this error while mounting in ubuntu 10.04 with my account

[[IMG]http://img163.imageshack.us/img163/3725/userpl.png[/IMG]]("http://img163.imageshack.us/i/userpl.png/")




so i log in using the **root account** and this is what i get

[[IMG]http://img215.imageshack.us/img215/7498/67952786.png[/IMG]]("http://img215.imageshack.us/i/67952786.png/")




--------------------------------

here is my 


**[COLOR=Red]sudo fdisk -lu[/COLOR]**

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05c105c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    38918879    19459408+   7  HPFS/NTFS
/dev/sda2        38918880    47219759     4150440    7  HPFS/NTFS
/dev/sda3        47231224    78140159    15454468    f  W95 Ext'd (LBA)
/dev/sda5        76174623    78140159      982768+  82  Linux swap / Solaris
/dev/sda6   *    47231226    76164164    14466469+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb440a66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1953520064   976760001    7  HPFS/NTFS



----------------
**[COLOR=Red]sudo blkid[/COLOR]**


/dev/sda1: UUID="C29CB9FB9CB9EA55" TYPE="ntfs" 
/dev/sda2: UUID="1D06C7F0DF20467F" TYPE="ntfs" 
/dev/sda5: TYPE="swap" 
/dev/sda6: UUID="86a5bd4a-a859-4e29-a081-0ef610515755" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="SimpleDrive" UUID="30B41082B4104D2A" TYPE="ntfs" 


------------------------

[COLOR=Red]**cat /etc/fstab**

[/COLOR]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda6 :
UUID=86a5bd4a-a859-4e29-a081-0ef610515755    /    ext3    defaults    01
#Entry for /dev/sda1 :
UUID=C29CB9FB9CB9EA55    /media/C29CB9FB9CB9EA55    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb1 :
UUID=30B41082B4104D2A    /media/Simple    ntfs-3g    defaults,locale=en_US.utf8    00
#Entry for /dev/sda2 :
UUID=1D06C7F0DF20467F    /media/sda2    ntfs    defaults,nls=utf8,umask=0222    00
UUID=    swap    swap    sw    0    0
/dev/sr0    swap    udf,iso9660    defaults    0    0

---

### Post by kgas on 2010-05-16
try to check the drive windows using chkdsk (as shown in the message) and then connect with your ubuntu installation also ensure that relevant ntfs package installed.Sometimes if you did not eject the drive in windows properly this may happen.

---

### Post by scouser73 on 2010-05-16
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by warfacegod on 2010-05-16
The first thing you need to try is plugging it back into a Windows machine and "Safely Remove Hardware". The icon for that can be found in the System Tray (the little icons on the bottom right of the screen).

---

### Post by optix7 on 2010-05-16
i have tried the above suggestions but it still wont mount. any more ideas ? none of the listed softwares helped either (NTFS Confg tools) (storage device manager) and (mount manager) :(

---

### Post by michy99 on 2010-05-16
Remove the entry in /etc/fstab and just let Ubuntu mount it automatically.

---

### Post by optix7 on 2010-05-17
> **michy99 said:**
> Remove the entry in /etc/fstab and just let Ubuntu mount it automatically.


still wont mount, got the same second window above :(

---

### Post by optix7 on 2010-05-18
I Solved this problem by removing all (NTFS-3G) files from the ubuntu software center :) it simply mounted again !

Thanks for the help again guys

---

