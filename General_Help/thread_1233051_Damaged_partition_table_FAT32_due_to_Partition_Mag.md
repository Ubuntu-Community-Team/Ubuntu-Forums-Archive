---
title: "Damaged partition table FAT32 due to Partition Magic misbehavior"
date: 2009-08-06
forum: General Help
---

### Post by cyrylski on 2009-08-06
Hello, 

I've recently bought myself a new HDD and installed the newest Ubuntu. On the previous one I had a Windows XP. I was playing a lot with copying data from the old to the new HDD and everything was fine up to one point. 

I had a 80GB HDD structured like this: 

partition 1: 3 GB (hidden recovery partition for ACER laptops, usesless)
partition 2: 35 GB (former windows parition)
partition 3: 35 GB (just a storage partition) labeled ACERDATA

what I tried to do was:

1) delete part. 1 and 2
2) move/resize part. 3 

Partiotion magic went smoothly through 1). The problem started when partition 3 was being modified. When the program was at 72% of resizing partition and 0% of moving data it got stuck. After some time of zero progress I resetted the machine (knowing laready it'll be a total mess-up).

the result is like that: 

Windows sees only one big partition of 70GB (as I wanted after resizing), labeled ACERDATA. Ubuntu sees it the same. 

Catalog structure in the root of ACERDATA is unaffected under Windows *but* files have realy strange names (random characters). One little folder seems unaffected, files in it have correct names.

Gparted recognizes it as fat32 but tells me the contents of the filesystem can't be read. 

Now, my questions is what can I do to revive this partition? 

I have my own suspicion that it was only the partition table (the "contents list") that was damaged, no files were physically moved. 

I tried testdisk analyses but I'm afraid to proceed with any actions in order not to make any further damage. Could you please give me a hint what to start with? I can draw you a picture in return :D and I'd be grateful :)

I'm using Ubuntu 8.04 and Windows XP, both bootable. My PC is an ACER laptop with 250GB hdd inside (bootable) and 80GB (the wrong one) on a USB adapter now.

---

### Post by louieb on 2009-08-06
Just a guess that the partition table is ok. Its the structure of the file-system inside the partition thats messed up. **photorec **may be your best open source solution.  available on the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") 

To check the partition table 

```
sudo fdisk -l 
```lowercase L at the end.

Please put the fdisk output in your next post.

---

### Post by cyrylski on 2009-08-06
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a89c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016    b  W95 FAT32
/dev/sda2            4864       27780   184080802+  83  Linux
/dev/sda3           27781       30212    19535040   83  Linux
/dev/sda4           30213       30401     1518142+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe911e911

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdb5               2        9729    78140128+   b  W95 FAT32


This is the output. the last two lines is the problematic stuff. Does it tell you anything?

I'll try photorec meanwhile. 

Thanks for replying ;)

update: 

photorec is running and is recovering files.

---

### Post by cyrylski on 2009-08-06
Ok, photorec helped me a little bit - it copied all the files it found on its way to my other disk. However the files are quite messy. they don't have names as previously but numbers instead. The numbers are given by photoRec. At least, I had a copy of all the files. Once this is secured I could try TestDisk.

I ran TestDisk in Terminal and I repaired the broken partition table. 

I took following steps:

in the terminal I ran testdisk:

```
# sudo testdisk
```

I chose 
```
[ Create ]  Create a new log file
```

and then selected my disk from the list 
```
Disk /dev/sdb - 80 GB / 74 GiB
```

it was an Intel Partition:
```
[Intel  ]  Intel/PC partition
```

after selecting it I proceeded and chose ```
[ Analyse  ]
``` and then proceeded further on. TestDisk asked me if it was a Vista partition. Nope, it wasn't. Then, I got a list like that: 

```
Disk /dev/sdb - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1   382 254 63    6152832 [PQSERVICE]
P FAT32 LBA              383   0  1  5030 254 63   74670120 [ACER]
L FAT32 LBA             5031   1  1  9728 254 63   75473307 [ACERDATA]
```

these were the partitions TestDisk found on the disk. I scrolled to the last one and ensured it had all the files I missed after :), by pressing P. Having done that, I pressed enter and proceeded. In the screen with partitions list 

```
Disk /dev/sdb - 80 GB / 74 GiB - CHS 9729 255 63

     Partition                  Start        End    Size in sectors

 1 * FAT32                    0   1  1   382 254 63    6152832 [PQSERVICE]
 2 P FAT32 LBA              383   0  1  5030 254 63   74670120 [ACER]
 3 E extended LBA          5031   0  1  9728 254 63   75473370
 5 L FAT32 LBA             5031   1  1  9728 254 63   75473307 [ACERDATA]

```  

I chose to write the partition tables to the disk and than rebooted. 
After rebooting the Disk was all in flying colors :)

Voila!

---

