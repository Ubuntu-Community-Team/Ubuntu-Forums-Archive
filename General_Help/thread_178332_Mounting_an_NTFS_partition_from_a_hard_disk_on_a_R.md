---
title: "Mounting an NTFS partition from a hard disk on a RAID controller"
date: 2006-05-17
forum: General Help
---

### Post by aoberoi on 2006-05-17
I was having trouble mounting my NTFS partition from the RAID controller on my MB.

I'm still pretty noob.. all ive done in ubuntu is c programming in a text editor like emacs and installed and updated a few packages...

any way... this is what i did..

output of fdisk -l:

> ankur@ankurpc:~$ sudo fdisk -l

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2330    18715693+  83  Linux
/dev/hdb2            2331        2434      835380    5  Extended
/dev/hdb5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       72961   586059201    7  HPFS/NTFS


then i added the last line into my /etc/fstab so it looked like this...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /mnt/winpart    ntfs    users,owner,ro,umask=000 0 0


i created the mountpoint earlier so /mnt/winpart DOES exist.

here is some other info that might help:
im using ubuntu 5.10 amd64
the MD is a ASUS K8V SE Deluxe
the RAID controller is the Promise FastTrack chipset PDC20378
its configured in RAID 0 (striping) and it is bootable with windows installed on the partition
theres one big partition made from 2 300GB seagate disks

if theres any other info needed to help... ill gladly post it up...

i hope someone has an idea and id appreciate any feedback...

thanks

---

### Post by aoberoi on 2006-05-17
i can see that theres a problem already because it should b seen as a 600GB disk.. not the 300GB it shows now...

just a starting place

---

### Post by aoberoi on 2006-05-18
i think the problem is related to finding the right driver for the Promise PDC20378 RAID controller... i dont really know the best place to look for something like that... any suggestions?

i found one site that said it was made for red hat and suse.. would there be any difference in using it for ubuntu?

any help appreciated

---

