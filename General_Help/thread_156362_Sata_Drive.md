---
title: "Sata Drive"
date: 2006-04-06
forum: General Help
---

### Post by Fatstink on 2006-04-06
I have a 300 GB sata drive that I would like to format, I believe it is located at /dev/sda5.  How do I format this device, preferably fat32, and mount it???

---

### Post by Sutekh on 2006-04-06
- You can install GParted, which is an easy to use partitioner.  
```
sudo apt-get install gparted
```
 - You should find it very easy to format the /dev/sda5 partition FAT32.  Just ensure that /dev/sda5 really is the one you need to format.

- Before you start you should unmount the partition
```
sudo umount /dev/sda5
```
 - Then you can create/manipulate the partition as you require.


 - On to the mounting.  You need to create a mount folder, this is where the partition will be mounted
```
sudo mkdir /mnt/fat32
```
 - call it whatever you like.

 - Then to mount it, you should edit the /etc/fstab - the configuration file for mounting partitions
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
 - To backup and edit the file

 - If you already have a line for /dev/sda5 then change it to the following, if one doesn't exist then add it
```
dev/sda5   /mnt/fat32   vfat   iocharset=utf8,umask=0000   0   0
```
 - Save the file (Ctrl+O) and exit (Ctrl+X).

 - Then remount the partitions with
```
sudo mount -a
```

---

### Post by Fatstink on 2006-04-06
it tells me

mount: special device /dev/sda5 does not exist

also when I tried to unmount it it didn't let me do so.  How do I format my drive to a Fat32???

---

### Post by Sutekh on 2006-04-06
Alright then the partition is not /dev/sda5.

You can list all the partitions on your hard discs using
```
sudo fdisk -l
```

Have you opened GParted yet to have a look?

---

### Post by Fatstink on 2006-04-06
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I get this message, it is actually sda.

How do I go about opening GParted??? And does it matter I am running KDE?

---

### Post by aysiu on 2006-04-06
[QUOTE=Fatstink]How do I go about opening GParted???[/quote] ```
sudo gparted
``` > And does it matter I am running KDE? No.

---

### Post by Sutekh on 2006-04-06
Did you install it yet?  

It shouldn't matter that you are using KDE.  The only issue is that if you install GParted then you install all the GTK libraries too.  You might not really want all that.

Now that you mention it could always install QTParted instead (won't require the GTK libraries).  Which would you rather?

---

### Post by Fatstink on 2006-04-06
I used GParted and it worked great however I still get the error

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Sutekh on 2006-04-06
[QUOTE=Fatstink]I used GParted and it worked great however I still get the error

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/QUOTE]
Cool.  

How about posting the output from```
sudo fdisk -l
``` and ```
cat /etc/fstab
```
So we can see the location of the FAT partition, and what changes you need to make to mount it.

---

### Post by Fatstink on 2006-04-06
Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3582    28772383+  83  Linux
/dev/hda2            3583        3738     1253070    5  Extended
/dev/hda5            3583        3738     1253038+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
16 heads, 63 sectors/track, 77557 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601   83  Linux
--------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda        /mnt/fat32      vfat    iocharset=utf8,umask=0000 0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Sutekh on 2006-04-06
[QUOTE=Fatstink]
/dev/sda       /mnt/fat32      vfat    iocharset=utf8,umask=0000 0       0[/QUOTE]
You need to include the partition number, not just /dev/sda.

Try 
```
/dev/sda**1 **       /mnt/fat32      vfat    iocharset=utf8,umask=0000  0  0     
```

---

### Post by Fatstink on 2006-04-07
Okay it mounted, now how do I get to it?

---

### Post by Sutekh on 2006-04-07
Well you can use KDE's all-in-one browser, Konqueror.  Just navigate from the root filesystem / to the mount folder /mnt/fat32.

Or you can use the terminal application, Konsole.  Use 'cd' to change directory, and other commands like cp (copy), mv(move), rm(remove), etc.

The 'How do I use the Terminal' link in my signature can help you around if you wan to use Konsole.

---

