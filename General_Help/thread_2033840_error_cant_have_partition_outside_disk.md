---
title: "error cant have partition outside disk"
date: 2012-07-27
forum: General Help
---

### Post by elliotn on 2012-07-27
plz anyone help me, my partitions are all messed up I can't boot, gparted sees the drive as one unallocated space....the drive contains very sensitive data in the 300gb ntfs partition

I tried the Gparted LiveCd with Test disk but its complicated

help plz  

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1f1295a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1         992   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2               1       12748   102396928    7  HPFS/NTFS
/dev/sda3           12749       52054   315722652+   7  HPFS/NTFS
/dev/sda4           52055       60802    70268310    f  W95 Ext'd (LBA)
/dev/sda5           54993       54994        6144    1  FAT12
/dev/sda6           57727       60541    22603776   83  Linux
/dev/sda7           60542       60802     2085880   82  Linux swap / Solaris

custom@custom:~$ sudo gpart /dev/sda

Begin scan...
Possible partition(Windows NT/W2K FS), size(308322mb), offset(99998mb)
Possible extended partition at offset(408323mb)
End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 308322mb #s(631445304) s(204796620-836241923)
   chs:  (1023/254/63)-(1023/254/63)d (12748/0/1)-(52053/166/21)r

Primary partition(2)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 66574mb #s(136343594) s(836247510-972591103)
   chs:  (1023/254/63)-(1023/254/63)d (52054/0/1)-(60540/254/2)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

custom@custom:~$ sudo parted /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) rescue                                                           
Error: Can't have a partition outside the disk!                           
(parted) rescu                                                            
Error: Can't have a partition outside the disk!                           
(parted) rescue print
Error: Can't have a partition outside the disk!                           
(parted)

---

### Post by Cheesemill on 2012-07-27
You could try using FixParts.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by elliotn on 2012-07-27
> **Cheesemill said:**
> You could try using FixParts.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

ok downloaded now how to I use it

---

### Post by Cheesemill on 2012-07-27
It explains everything in the link that I gave you.

---

### Post by elliotn on 2012-07-27
>  custom@custom:~$ sudo fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0xF1F1295A
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                    16         1999   primary              Y      0x83
   2      *           2048    204796619   primary              Y      0x07
   3             204796620    836241924   primary              Y      0x07
   5             883458048    883470335   logical     Y               0x01
   6             927383552    972591103   logical     Y               0x83
   7             972599296    976771055   logical     Y               0x82

MBR command (? for help): 

 

help guys I don't c what to do here

---

### Post by MSPdwalt on 2012-07-27
Well, how exactly did it get messed up in the first place?  You would use this tool to undo the damage.

Did you improperly re-size a partition or something?

---

### Post by elliotn on 2012-07-27
> **MSPdwalt said:**
> Well, how exactly did it get messed up in the first place?  You would use this tool to undo the damage.

Did you improperly re-size a partition or something?

I way trying to install windows XP so I can triple boot Ubuntu, windows 7 and XP but XP installed well in the partition that was ext4 I formated it with Gparted into NTFS then I reformatted it again into NTFS with the XP CD.... when XP rebooted I couldn't boot anymore. so I put my remastered CD of Ubuntu and Gparted said the drive is UNALLOCATED SPACE

now I can boot into Ubuntu but my 300Gb partition will all very life threatening space has an exclamation mark in Gparted.

I tried ntfs-3g but it fails

---

### Post by efflandt on 2012-07-27
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1f1295a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1         992   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2               1       12748   102396928    7  HPFS/NTFS
/dev/sda3           12749       52054   315722652+   7  HPFS/NTFS
/dev/sda4           52055       60802    70268310    f  W95 Ext'd (LBA)
/dev/sda5           54993       54994        6144    1  FAT12
/dev/sda6           57727       60541    22603776   83  Linux
/dev/sda7           60542       60802     2085880   82  Linux swap / SolarisWhatever you used to create partitions somehow ended extended partition sda4 and logical partition sda7 on cyl 60802 when fdisk says you only have 60801 cylinders.

Not sure how comfortable you are using fdisk, but I would use it to remove the logical partitions and sd4, recreate them as:

/dev/sda4           52055       **60801** type    f
 /dev/sda5           54993       54994 type    1
 /dev/sda6           57727       60541 type   83
 /dev/sda7           60542       **60801** type   82

and then: **sudo mkswap /dev/sda7** (check its blkid and update etc/fstab on on that system if necessary).  That normally should not affect data for partitions recreated exactly like they were, but I have been using Linux fdisk for over 15 years and it could risk data on altered partitions if you make a mistake.

---

### Post by elliotn on 2012-07-30
I guess I should mark this thread as solved, thanks to Test Disk, Fixparts and parted, recuva and Gparted live CD I manage to fix and boot to Ubuntu then used Windows 7 disk to fix the Win7 boot and chkdsk to fix the 300gb partition although I lost data am busy with Recuva recovering some data.

---

### Post by MSPdwalt on 2012-07-30
Word of advice next time you want to multi-boot, start with your oldest version of Windows first, then go upwards until you're done with windows, THEN install Linux.

Doing it in random order is asking for trouble.

---

