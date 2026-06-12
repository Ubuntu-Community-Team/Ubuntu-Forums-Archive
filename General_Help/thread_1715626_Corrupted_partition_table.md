---
title: "Corrupted partition table"
date: 2011-03-27
forum: General Help
---

### Post by lojtas on 2011-03-27
Hello, I deleted one of partitions using Ubuntu disk utility. Now I can't use freed space, because disk utility returns error: ```
Invalid partition table on /dev/sda -- wrong signature 0.
``` I installed GParted, but it doesn't see any partitions. Parted output is as follows: ```
sudo LANG=C parted -l
[sudo] password for: 
Error: Invalid partition table on /dev/sda -- wrong signature 0.          
Ignore/Cancel? Ignore                                                     
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  30.7GB  30.7GB  primary   ext4         boot
 2      30.7GB  320GB   289GB   extended
 5      30.7GB  281GB   250GB   logical   ext4
 6      311GB   320GB   9000MB  logical

``` Fdisk shows the same with comment "omitting empty partition (7)". Also I tried to analyze disk with testdisk, but I don't understand output (it's attached). Before messing with disk it looked like this:
[LIST]
[*]sda1 - ubuntu
[*]sda2 - extended
[*]sda5 - home
[*]sda6 - not used (left if 2nd OS would be needed), deleted one
[*]sda7 - swap, now showing as sda6
[/LIST]
Is it possible to somehow repair it without reformating sda2 (home there)?

---

### Post by srs5694 on 2011-03-27
It sounds like the data that defines one of the logical partitions has become damaged. If you could post the output of "sudo fdisk -lu", it's conceivable that we could guess at what it should be, but any such guess is far from guaranteed to be correct. There's also a very slim chance that my [FixParts](http://www.rodsbooks.com/fixparts/) program could recover the lost partition; however, it wasn't designed for this task, so it might not work. It won't damage the disk so long as you do *not* use the 'w' command in its menu.

Before you do anything else, though, I recommend you issue this command:

```

sudo sfdisk -d /dev/sda > parts.txt

```

Copy the resulting parts.txt file to a USB flash drive, floppy disk, CD-R, or some other removable medium. You might as well post the file here, too; as with FixParts, there's a slim chance that sfdisk will do better at interpreting your partitions than parted or fdisk. Having the parts.txt file will serve as insurance; it can recover the partitions that have not been lost in case you make matters worse. Be aware, though, that this backup will preserve only those partitions that sfdisk can read, not including whatever damaged data may still lurk on the hard disk.

---

### Post by lojtas on 2011-03-27
Srs5694, I post outputs you asked:
1) sfdisk -d
```
sudo LANG=C sfdisk -d /dev/sda > sfdisk.txt
[sudo] password for: 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 548973180 does not have an msdos signature

```
2) sfdisk.txt
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 59998208, Id=83, bootable
/dev/sda2 : start= 60002302, size=565139458, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 60002304, size=488966144, Id=83
/dev/sda6 : start=607563776, size= 17577984, Id=82
```
3) fdisk -lu
```
sudo LANG=C fdisk -lu
[sudo] password for: 
omitting empty partition (7)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab30f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    60000255    29999104   83  Linux
/dev/sda2        60002302   625141759   282569729    5  Extended
/dev/sda5        60002304   548968447   244483072   83  Linux
/dev/sda6       607563776   625141759     8788992   82  Linux swap / Solaris

```
4) fixparts 
```
sudo fixparts /dev/sda
[sudo] password for: 
FixParts 0.7.1

Loading MBR data from /dev/sda
MBR signature in logical partition invalid; read 0x0000, but should be 0xAA55
Segmentation fault

```

---

### Post by LostFarmer on 2011-03-27
> sfdisk: ERROR: sector 548973180 does not have an msdos signature  Need to verify that sector, from a root terminal or use 'sudo' and run
```
dd if=/dev/sda count=1 bs=512 skip=548973180 |hexdump
```  Need to see on last line displayed and last digets on line 'aa55'. Better just post the last 4 lines 'lines 1c0 to 1f0', help use to be sure of sector.  

should look like: 
```
00001c0 ffff fe07 ffff 0002 0000 98b5 0270 fe00
00001d0 ffff fe05 ffff 98b7 0270 7b74 030d 0000
00001e0 0000 0000 0000 0000 0000 0000 0000 0000
00001f0 0000 0000 0000 0000 0000 0000 0000** aa55**

```If the 'aa55' is missing, the only way I know of is to manually save the dd output to a file, edit the file then use dd to write it back.  If that is needed use Synaptic Package Manager and install 'BLESS HEX EDITOR', and wait for advice on how to do above. Some one may have a better/safer way.

---

### Post by srs5694 on 2011-03-27
I've re-read your original post. If I understand correctly, the lost partition was not being used and so contains no useful data. If so, I recommend this as a recovery method, using the sfdisk.txt file you created earlier:

```

sudo sfdisk -f /dev/sda < sfdisk.txt

```

Since sfdisk saw all your good partitions and had problems only with the partition you aren't using, this command will write back your partition table without the errors that are causing GParted and Disk Utility problems. You should then be able to use one of these tools (or fdisk or various others) to create a new partition in that space.

Be aware, however, that since your disk is currently damaged, anything you do with it carries added risk. I recommend you back up your most important files (and preferably the whole computer) before you attempt any sort of recovery.

---

### Post by lojtas on 2011-03-29
I got busy cleaning my disk and making backup. Then I used ```
sudo sfdisk -f /dev/sda < sfdisk.txt
``` to rewrite partition table. It worked smoothly and I could allocate and format free space with GParted. Sfdisk, fdisk, GParted don't return any errors. Before rewriting partition table in corrupted sector were all zeros. Now it looks like this: ```
sudo dd if=/dev/sda count=1 bs=512 skip=548973180 | hexdump > hex.txt

``````
hex.txt:
00001b0 0000 0000 0000 0000 0000 0000 0000 fe00
00001c0 ffff fe83 ffff 003f 0000 0a5d 0356 fe00
00001d0 ffff fe05 ffff 251a 207b f4e3 0027 0000
00001e0 0000 0000 0000 0000 0000 0000 0000 0000
00001f0 0000 0000 0000 0000 0000 0000 0000 aa55
0000200
``` So it's correct. 
Thank you very much for quick help! I appreciate it.

---

