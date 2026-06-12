---
title: "ive got 18 million Tera bytes : .("
date: 2012-01-21
forum: General Help
---

### Post by fluft on 2012-01-21
hello : )

Disk utility says that my 320 gig HD has a partition at the end of the table that is 18446744 TB in size.  however all the other partitions ( ubuntu and xp osx are showing healthy)

pictures from  testdisk and disk utility

[IMG]http://i85.photobucket.com/albums/k76/generalphotos/partitiontablepic2.jpg[/IMG]

However, allthough these programs can see the HD o.k, Gparted says the same disk has 298 unallocated and states:

"
total sectors 625142449

WARNING 

cannot have a partition outside the disk!!"


so gparted cannot help me delete that troubled partition . i tryed an xp CD to see if i can access the bad partition to delete it , unfortunately it is not showing up, so i can not delete it, I can only see it in ubuntu disk utility and test disk seems to have two extra partitions with 'X' next to them. and i think this is causing problems with grub2.

any ideas how to delete that partition(s) can i use testdisk? is this wise?

thanks :)

---

### Post by Rubi1200 on 2012-01-21
What do the following command show?

```
sudo fdisk -lu

sudo parted -l
```

---

### Post by fluft on 2012-01-21
hello

sudo fdisk -lu =

[PHP]Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55220035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    55295729    27647833+   7  HPFS/NTFS
/dev/sda2        55295730    63488879     4096575    7  HPFS/NTFS
/dev/sda3        63488943   176136659    56323858+   7  HPFS/NTFS
/dev/sda4       176136660   625153409   224508375    f  W95 Ext'd (LBA)
/dev/sda5       176136723   319500714    71681996   af  HFS / HFS+
/dev/sda6       319502336   327313391     3905528   82  Linux swap / Solaris
/dev/sda7       327315456   625141759   148913152   83  Linux

Disk /dev/sdb: 164.7 GB, 164695473664 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321670847 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32bce1a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   258746732   129373335    7  HPFS/NTFS
/dev/sdb2   *   258746733   321667478    31460373   af  HFS / HFS+
 [/PHP]


sudo parted -l =
Error: Cannot have a partition outside the disk!                          

Model: ATA HDS722516VLSA80 (scsi)
Disk /dev/sdb: 165GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  132GB  132GB   primary  ntfs
 2      132GB   165GB  32.2GB  primary  hfs+         boot


additional

Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.





: /

---

### Post by fluft on 2012-01-21
yet here is what gparted shows: 

[IMG]http://i85.photobucket.com/albums/k76/generalphotos/gparted.jpg[/IMG]

---

### Post by Quackers on 2012-01-22
The partition highlighted in red is your problem. The extended partition finishes after the last sector of your hard drive, which is impossible.
Gparted is confused.
You can fix this by using srs5694's little utility Fixparts as described below
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total [COLOR="Red"]625142448 sectors[/COLOR]
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55220035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    55295729    27647833+   7  HPFS/NTFS
/dev/sda2        55295730    63488879     4096575    7  HPFS/NTFS
/dev/sda3        63488943   176136659    56323858+   7  HPFS/NTFS
/dev/sda4       176136660   [COLOR="Red"]625153409[/COLOR]   224508375    f  W95 Extd (LBA)
/dev/sda5       176136723   319500714    71681996   af  HFS / HFS+
/dev/sda6       319502336   327313391     3905528   82  Linux swap / Solaris
/dev/sda7       327315456   625141759   148913152   83  Linux
```

---

### Post by xyzzyman on 2012-01-22
I hate to use all caps but BACKUP YOUR DATA before trying fixparts.

---

### Post by fluft on 2012-01-22
> **Quackers said:**
> The partition highlighted in red is your problem. The extended partition finishes after the last sector of your hard drive, which is impossible.
Gparted is confused.
You can fix this by using srs5694's little utility Fixparts as described below
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total [COLOR="Red"]625142448 sectors[/COLOR]
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55220035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    55295729    27647833+   7  HPFS/NTFS
/dev/sda2        55295730    63488879     4096575    7  HPFS/NTFS
/dev/sda3        63488943   176136659    56323858+   7  HPFS/NTFS
/dev/sda4       176136660   [COLOR="Red"]625153409[/COLOR]   224508375    f  W95 Extd (LBA)
/dev/sda5       176136723   319500714    71681996   af  HFS / HFS+
/dev/sda6       319502336   327313391     3905528   82  Linux swap / Solaris
/dev/sda7       327315456   625141759   148913152   83  Linux
```

Thanks Quackers! : )  I was so worried, I just did not see that , well spotted. I shall give it try today! hope at last : P

---

### Post by fluft on 2012-01-22
> **xyzzyman said:**
> I hate to use all caps but BACKUP YOUR DATA before trying fixparts.

Yes indeed xyzzyman! I shall find room on another drive ! thanks for reminding me that its not 100 % safe. Good idea.

: ) ( p.s at times like these, caps lock is our friend  : )

---

### Post by fluft on 2012-01-22
Ive added screen shots below.  

Hi,

i was able to get the partitions sorted. but i can not get into windows from grub2 

so i try this :

sudo lilo -M /dev/sda mbr

after which grub2 is gone, but i can get into my windows OS O.k.

so i try to reinstall grub2 from a live cd

sudo mount /dev/sda7 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda

And then i can get back to ubuntu from the new grub2 menu.

but again i cant get into windows from the grub2 menu (although windows is listed in grub, it reports an error) 

any ideas guys : ?

---

### Post by fluft on 2012-01-22
here are the results : 

[IMG]http://i85.photobucket.com/albums/k76/generalphotos/Screenshot-2.jpg[/IMG]

[IMG]http://i85.photobucket.com/albums/k76/generalphotos/diskutility.jpg[/IMG]

grub just cannot connect to the windows partitions correctly. : /

---

### Post by xyzzyman on 2012-01-22
Have you now done a ```
sudo update-grub
``` from within Ubuntu? And can you browse the windows partition from Ubuntu? It says you're only using 4.55GB's in SDA1 so I'm assuming it's XP? That can't be vista or Win7 unless the partition is corrupt.

---

