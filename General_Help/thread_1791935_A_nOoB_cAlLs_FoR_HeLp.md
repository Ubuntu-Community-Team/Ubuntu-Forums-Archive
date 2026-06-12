---
title: "A nOoB cAlLs FoR HeLp?????????????????"
date: 2011-06-27
forum: General Help
---

### Post by upadhyay.minmay on 2011-06-27
guys i just wanted to know the name of the directory of my bluetooth device. By default it is /dev/mobilephone

for example /dev/rfcomm0


actually when i use gsmsendsms -d /dev/mobilephone
inspired by page- [http://ubuntuforums.org/showthread.php?t=1199026](http://ubuntuforums.org/showthread.php?t=1199026)
 
terminal replies there is no such directory,
so how may i get the name of that directory



and guys i m a supernoob so please dont laugh at my quest.

---

### Post by nzjethro on 2011-06-27
> **upadhyay.minmay said:**
> 
so how may i get the name of that directory

Hi upadhyay, welcome to the forums. If you run (in a terminal) the command
```
sudo fdisk -l
```
(that's a lowercase L), it will show you a list of all you devices.
The output should start with a line like this:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes

```
which is saying that /dev/sda is 320GB in size (my HDD). It then run's through each of the partitions on this drive, then onto the next drive. Each subsequent drive will have a similar line, with the name (/dev/sdX), and the size of the drive.
Simply scroll through until you find a device that matches your mobile phone (in terms of size etc.), and then note what /dev/sdX is. This is the directory to your phone.

Note, if you want to access any files on the phone, you will have to mount the phone, using:
> sudo mount /dev/sdX /mnt
Then run all of your commands on the folder /mnt.

Another note, please in future use a more descriptive title to you thread. There may be others with a similar problem, and it is easier for them to locate the solution if the thread has a title such as "How do I find the directory of my bluetooth device".
:)

---

### Post by upadhyay.minmay on 2011-06-27
sorry about the title
sudo fdisk-l provides the following results


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00190019

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       38913   286969095    f  W95 Ext'd (LBA)
/dev/sda5            3188       14660    92156841    7  HPFS/NTFS
/dev/sda6           14661       26133    92156841    7  HPFS/NTFS
/dev/sda7           26134       38587   100036723+   7  HPFS/NTFS

all results like /dev/sdX are only the partitions of my HDD
there is no such mobile device listed

---

