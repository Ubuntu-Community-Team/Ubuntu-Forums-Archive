---
title: "Gparted won't read partition table"
date: 2011-08-29
forum: General Help
---

### Post by scott_g on 2011-08-29
Hi,

I've been Googling for a while, but can't seem to figure this one out.  

I'm running Ubuntu 10.04, and haven't changed anything related to the hard drive in question.

When I run 'fdisk -l /dev/sdf', I get:
```

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36374d68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      182401  1465136001   83  Linux
```

However, gparted won't read the partition table; it throws an error of:
```

======================
libparted : 2.2
======================
Partition 1 isn't aligned to cylinder boundaries.  This is still unsupported.
```

Does anyone know how to fix this?

I forced a fsck of the partition, and it is in progress, but it hasn't turned up anything yet.

Thanks in advance,
Scott

---

### Post by 23dornot23d on 2011-08-29
Update libparted ...... mine is version 3.0 ...... might make a deifference .....

yours is quite old now .....  2.2 

[http://gparted.sourceforge.net/news.php](http://gparted.sourceforge.net/news.php)

Just the first thing I would do - to make sure its not related to the older gparted.

---

### Post by Slim Odds on 2011-08-29
> **scott_g said:**
> Hi,

I've been Googling for a while, but can't seem to figure this one out.  

I'm running Ubuntu 10.04, and haven't changed anything related to the hard drive in question.

When I run 'fdisk -l /dev/sdf', I get:
```

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36374d68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      182401  1465136001   83  Linux
```However, gparted won't read the partition table; it throws an error of:
```

======================
libparted : 2.2
======================
Partition 1 isn't aligned to cylinder boundaries.  This is still unsupported.
```Does anyone know how to fix this?

I forced a fsck of the partition, and it is in progress, but it hasn't turned up anything yet.

Thanks in advance,
Scott

What did you use to create the partition?

Just so you know, fsck stands for "File System CHeck". So it checks files systems ***within*** a partition. So it's not going to find any problem ***with* **a partition.

---

### Post by scott_g on 2011-08-29
Hmm, good point.  I had forgotten that gparted didn't support ext3 partitions >1TB when I created it, so I had to do it through the command line.  I don't remember what the commands were, but I didn't create it with gparted.  So I guess it's always been like this, and if I want to modify it, I'd have to use a different program?

If I convert it to an ext4, would it be supported by gparted?

And thanks for clarifying fsck; it was just my go-to tool for checking hard drive errors.

---

### Post by oldfred on 2011-08-29
Drives have not used cylinder since they became larger than 8GB. BIOS changed to use LBA or large block allocation. 

New drives now should be on 8 sector boundries and now start at sector 2048 where they used to start at sector 63.

Ignore any errors about cylinder alignment. The very newest versions do not give that error.

---

### Post by scott_g on 2011-08-30
Thanks for the info; always good to learn something new.

I have an ext4 partition that gparted has not trouble with, so I'll try converting the ext3 partition to an ext4, and see if it can read it.

Thanks for the help; I'll post an update with how it turned out.

Scott

---

### Post by scott_g on 2011-08-30
Well, that didn't seem to do a whole lot; gparted still doesn't read anything.  It just shows the drive as unallocated space.  I'm actually trying to re-size the existing partition by 50GB and make a new one that's 50GB at the end.  The hope was to create a software raid between two 50GB partitions on different disks for backups.  

So, is there a) a way to do this without gparted?  or b) a way to get gparted to see my partition?

Scott

---

### Post by dcstar on 2011-08-30
> **scott_g said:**
> Well, that didn't seem to do a whole lot; gparted still doesn't read anything.  It just shows the drive as unallocated space.  I'm actually trying to re-size the existing partition by 50GB and make a new one that's 50GB at the end.  The hope was to create a software raid between two 50GB partitions on different disks for backups.  

So, is there a) a way to do this without gparted?  or b) a way to get gparted to see my partition?

Scott

Run **sudo parted** from the command line and see what the messages are.

---

### Post by scott_g on 2011-08-30
I ran:

```
sudo parted /dev/sdf1
```

then a 'print' and got:

```
Model: Unknown (unknown)
Disk /dev/sdf1: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1500GB  1500GB  ext4
```

I've never used parted from the cli; not sure what else to do with it.  Does it support ext4?

Scott

---

### Post by dcstar on 2011-08-30
> **scott_g said:**
> I ran:

```
sudo parted /dev/sdf1
```

then a 'print' and got:

```
Model: Unknown (unknown)
Disk /dev/sdf1: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1500GB  1500GB  ext4
```

I've never used parted from the cli; not sure what else to do with it.  Does it support ext4?

Scott

Do not select specific partitions, select the device.

---

### Post by scott_g on 2011-08-30
> **dcstar said:**
> Do not select specific partitions, select the device.

OK, I tried that.  It gives:
```

GNU Parted 2.2
Using /dev/sdf
Welcome to GNU Par
(parted) print    
No Implementation: Partition 1 isn't aligned to cylinder boundaries.  This is
still unsupported.

```

Thanks for the help - what time is it in Australia?

Scott

---

### Post by scott_g on 2011-08-30
So I tried downloading the newest gparted live cd (uses Parted 2.3 apparently), but it gave the same result.  I also tried starting up the 11.04 live cd, but couldn't get it to run for some reason.

Currently, I'm trying to fixing the issue by getting the 50GB of space from another hard drive (I have plenty to choose from if you read my signature).

I'm still interested in finding out why gparted doesn't like to read my 1.5TB drive, if anyone else has more ideas.

Thanks for all of your help.
Scott

---

### Post by dcstar on 2011-09-01
> **scott_g said:**
> 
.......
I'm still interested in finding out why gparted doesn't like to read my 1.5TB drive, if anyone else has more ideas.


Check you system BIOS and see if had been reset to defaults or the hard drive settings have changed from Autodetect.

Also use the Disk Utility to check the SMART status to see if any blocks have been remapped - possibly if a critical block at the start of the partition has been remapped then Gparted may not be able to handle that.

---

### Post by YesWeCan on 2011-09-01
Partition table: loop?
What's the output of sfdisk -luS?

---

### Post by scott_g on 2011-09-01
> **dcstar said:**
> Check you system BIOS and see if had been reset to defaults or the hard drive settings have changed from Autodetect.

Also use the Disk Utility to check the SMART status to see if any blocks have been remapped - possibly if a critical block at the start of the partition has been remapped then Gparted may not be able to handle that.

I haven't changed anything in the BIOS. My motherboard was originally from an HP desktop, so it's pretty locked down.  The only options available to me is to reset to default settings.

I opened the disk utility, and have attached a screenshot of what I think is the relevant section?  

> **YesWeCan said:**
> Partition table: loop?
What's the output of sfdisk -luS?

I tried running parted on a different drive and got partition table: msdos - this seems to be more of the standard?  Is this why gparted won't read it?

Relevant output of 'sfdisk -luS' is:
```
Disk /dev/sdf: 182401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdf1            63 2930272064 2930272002  83  Linux
/dev/sdf2             0         -          0   0  Empty
/dev/sdf3             0         -          0   0  Empty
/dev/sdf4             0         -          0   0  Empty

```

Rest of the output (in case it's important?) is:
```

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 469820924  469820862   7  HPFS/NTFS
/dev/sda2     469836990 488392064   18555075   c  W95 FAT32 (LBA)
		start: (c,h,s) expected (1023,254,63) found (1022,0,1)
		end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1            63   2104514    2104452  82  Linux swap / Solaris
/dev/sdb2       2104515 976768064  974663550  83  Linux
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/sdc: 4865 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1            63  78156224   78156162  83  Linux
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

Disk /dev/sdd: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1            63 1851121754 1851121692  83  Linux
/dev/sdd2     1851121755 1953520064  102398310  fd  Linux raid autodetect
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty

Disk /dev/sde: 7297 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sde1   *        63  29141909   29141847  83  Linux
/dev/sde2      29141910 117226304   88084395  83  Linux
/dev/sde3             0         -          0   0  Empty
/dev/sde4             0         -          0   0  Empty

Disk /dev/sdf: 182401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdf1            63 2930272064 2930272002  83  Linux
/dev/sdf2             0         -          0   0  Empty
/dev/sdf3             0         -          0   0  Empty
/dev/sdf4             0         -          0   0  Empty

Disk /dev/sdg: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdg1            63 3804625754 3804625692  83  Linux
/dev/sdg2     3804625755 3907024064  102398310  fd  Linux raid autodetect
/dev/sdg3             0         -          0   0  Empty
/dev/sdg4             0         -          0   0  Empty

Disk /dev/md0: 12799770 cylinders, 2 heads, 4 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md0: unrecognized partition table type
No partitions found
```

Thanks for your help with this - I really appreciate it.

Scott

---

### Post by YesWeCan on 2011-09-01
The sfdisk output looks ok...
I don't know why the PT is being called "loop" and I don't know if it matters. I'm not much help. ;)
But I would like to see the whole MBR so I can try to find out what is different from usual. Would you mind posting
[COLOR="Navy"]sudo dd if=/dev/sdf bs=512 count=1 | hexdump -C[/COLOR]
The dd command is very dangerous so please copy it carefully.

---

### Post by scott_g on 2011-09-01
> **YesWeCan said:**
> The sfdisk output looks ok...
I don't know why the PT is being called "loop" and I don't know if it matters. I'm not much help. ;)
But I would like to see the whole MBR so I can try to find out what is different from usual. Would you mind posting
[COLOR="Navy"]sudo dd if=/dev/sdf bs=512 count=1 | hexdump -C[/COLOR]
The dd command is very dangerous so please copy it carefully.

The output is included below.  Is this what you were expecting?

```


00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
1+0 records in
1+0 records out
*
512 bytes (512 B) copied000000d0  00 00 00 00 00 00 00 00  00 00 00 00 82 18 52 12  |..............R.|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
, 7.8781e-05 s, 6.5 MB/s
000001b0  00 00 00 00 00 00 00 00  68 4d 37 36 00 00 00 01  |........hM76....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 02 67 a8 ae 00 00  |......?....g....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by YesWeCan on 2011-09-02
I don't see anything wrong with the MBR.

In post #2 23dornot23d suggested upgrading to parted 2.3 or higher. Have you tried that?

---

### Post by scott_g on 2011-09-02
> **YesWeCan said:**
> I don't see anything wrong with the MBR.

In post #2 23dornot23d suggested upgrading to parted 2.3 or higher. Have you tried that?

Yep, I did try it...  refer to post 12 for the details. End result was the same, it gave the same error.

Is there anyway to change the partition type/label from loop to msdos without destroying the data on the drive?

Scott

---

### Post by YesWeCan on 2011-09-02
> **scott_g said:**
> Yep, I did try it...  refer to post 12 for the details. End result was the same, it gave the same error.

Is there anyway to change the partition type/label from loop to msdos without destroying the data on the drive?

Scott
Missed that, sorry. Well, you could copy the MBR from another disk that works ok **without** copying its partition table. Back up the sdf PT just in case:
[COLOR="Navy"]sudo sfdisk -d /dev/sdf > sdfPT.bin[/COLOR]

Then copy from another drive sdx
[COLOR="navy"]sudo dd if=/dev/sdx bs=446 count=1 of=/dev/sdf
sudo hdparm -z /dev/sdf[/COLOR]

So this would make your sdf MBR the same as a working drive's but with a different partition size. If that still fails the problem would have to be related to the partition table entry, unless parted is using some data unrelated to the MBR.

---

### Post by scott_g on 2011-09-02
> **YesWeCan said:**
> Missed that, sorry. Well, you could copy the MBR from another disk that works ok **without** copying its partition table. Back up the sdf PT just in case:
[COLOR="Navy"]sudo sfdisk -d /dev/sdf > sdfPT.bin[/COLOR]

Then copy from another drive sdx
[COLOR="navy"]sudo dd if=/dev/sdx bs=446 count=1 of=/dev/sdf
sudo hdparm -z /dev/sdf[/COLOR]

So this would make your sdf MBR the same as a working drive's but with a different partition size. If that still fails the problem would have to be related to the partition table entry, unless parted is using some data unrelated to the MBR.

Success!!!

The final sequence of commands I ran were:
```

sudo sfdisk -d /dev/sdf > sdfPT.bin
sudo dd if=/dev/sdf bs=446 count=1 of=/home/scott/sdf.image
sudo dd if=/dev/sdg bs=446 count=1 of=/dev/sdf
sudo eject /dev/sdf
sudo hdparm -z /dev/sdf

```

When I open gparted, it now reads the partition fine.

fdisk -l reads:
```

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c7cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      182401  1465136001   83  Linux

```

sudo sfdisk -l reads:
```

Disk /dev/sdf: 182401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdf1          0+ 182400  182401- 1465136001   83  Linux
/dev/sdf2          0       -       0          0    0  Empty
/dev/sdf3          0       -       0          0    0  Empty
/dev/sdf4          0       -       0          0    0  Empty

```

parted /dev/sdf | print reads:
```

Model: ATA WDC WD15EADS-00P (scsi)
Disk /dev/sdf: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1500GB  1500GB  primary  ext4

```

Thank you for all of your help; I'm very glad it worked.

Scott

---

### Post by YesWeCan on 2011-09-02
Glad that worked. I wish I knew *why* it worked tho. :-k
I created a exact duplicate of your original MBR on a drive in  VirtualBox and parted recognized it as msdos. Weird.

---

### Post by scott_g on 2011-09-02
Hmm, I'm not sure.  Do you want copies of the image/bin files I made when I backed up the MBR?

So by doing that, we replaced the MBR, but didn't touch the partition table?  I'm a little confused how a hard drive is structured...

---

### Post by Slim Odds on 2011-09-02
> **scott_g said:**
> Hmm, I'm not sure.  Do you want copies of the image/bin files I made when I backed up the MBR?

So by doing that, we replaced the MBR, but didn't touch the partition table?  I'm a little confused how a hard drive is structured...

Have fun: [https://secure.wikimedia.org/wikipedia/en/wiki/Master_boot_record](https://secure.wikimedia.org/wikipedia/en/wiki/Master_boot_record)

---

### Post by dcstar on 2011-09-03
> **scott_g said:**
> 
So by doing that, we replaced the MBR, but didn't touch the partition table?  I'm a little confused how a hard drive is structured...

The Partition Table starts at byte 447 of the first 512 byte block.

---

