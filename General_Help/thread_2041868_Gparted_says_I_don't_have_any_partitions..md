---
title: "Gparted says I don't have any partitions."
date: 2012-08-13
forum: General Help
---

### Post by krytorii on 2012-08-13
My partition numbers were all over the place, so I followed [this guide]("http://journalxtra.com/linuxsanity/how-to-reorder-linux-drive-partition-numbers-2768/").

I can still boot into the kubuntu partition, and dolphin says my partitions still exist, however I can't help but notice this:

[IMG]http://ubuntuone.com/0GOoK1E27g3htRb644bpXG[/IMG]

I think I may have a problem...

---

### Post by oldfred on 2012-08-13
What does yellow diamond warning say. Click or maybe right click on it and it may tell why it has issues.

Was drive in RAID before? Post this also:
```

sudo fdisk -lu
```

---

### Post by krytorii on 2012-08-13
> **oldfred said:**
> What does yellow diamond warning say. Click or maybe right click on it and it may tell why it has issues.

Was drive in RAID before? Post this also:
```

sudo fdisk -lu
```

No RAID as far as I know, I did have a second hard drive but that's currently sat there, not plugged in.

The warning was "unable to satisfy all constraints on this partition".

The output from fdisk is:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes                                                                                                                          
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors                                                                                                
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                 
Sector size (logical/physical): 512 bytes / 4096 bytes                                                                                                                 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes                                                                                                                    
Disk identifier: 0x000e061c                                                                                                                                            
                                                                                                                                                                       
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    12582911     6290432    c  W95 FAT32 (LBA)
/dev/sda2   *    12582912   773597183   380507136    7  HPFS/NTFS/exFAT
/dev/sda3       773597184  1140860927   183631872    7  HPFS/NTFS/exFAT
/dev/sda4      1672341504  1953523711   140591104    5  Extended
/dev/sda5      1751298048  1812738047    30720000   83  Linux
/dev/sda6      1898229760  1949429759    25600000   83  Linux
/dev/sda7      1949429760  1953523711     2046976   82  Linux swap / Solaris

```

---

### Post by krytorii on 2012-08-13
I just had a look at [http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

#23 does not seem to apply to me, I didn't move any partitions so I can't have the problem with space between them.

---

### Post by oldfred on 2012-08-13
I did not know it was two sectors between logicals. But sda6 & sda7 only have one, so that may be the issue.

Backup partition table.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

I have not seen that particular error. But you can try these partition tools.

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

And maybe testdisk.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

And you can directly edit the sfdisk text file & read it back in.
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

---

### Post by krytorii on 2012-08-13
I'll have a proper go when I get a chance, thank you for the help :D

The parted tool does however print "Error: Unable to satisfy all constraints on the partition." whenever I try to do anything however.

The partition table I've backed up, just in case it's in any way relevant or useful:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 12580864, Id= c
/dev/sda2 : start= 12582912, size=761014272, Id= 7, bootable
/dev/sda3 : start=773597184, size=367263744, Id= 7
/dev/sda4 : start=1672341504, size=281182208, Id= 5
/dev/sda5 : start=1751298048, size= 61440000, Id=83
/dev/sda6 : start=1898229760, size= 51200000, Id=83
/dev/sda7 : start=1949429760, size=  4093952, Id=82

```

---

### Post by marlow59 on 2012-08-13
try also to run a memtest, it may output more relevant and explicit errors.

---

### Post by krytorii on 2012-08-14
> **marlow59 said:**
> try also to run a memtest, it may output more relevant and explicit errors.
 
I don't see how running a test on the ram is relevent?

Also, on fixparts, the swap partition is listed as omitted. The fixparts documentation doesn't really mention what to do in this case.

```
Disk size is 1953525168 sectors (931.5 GiB)                                                                                                                            
MBR disk identifier: 0x000E061C                                                                                                                                        
MBR partitions:                                                                                                                                                        
                                                                                                                                                                       
                                                   Can Be   Can Be                                                                                                     
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code                                                                                             
   1                  2048     12582911   primary              Y      0x0C                                                                                             
   2      *       12582912    773597183   primary              Y      0x07                                                                                             
   3             773597184   1140860927   primary              Y      0x07
   5            1751298048   1812738047   logical     Y               0x83
   6            1898229760   1949429759   logical     Y               0x83
   7            1949429760   1953523711   omitted                     0x82

```

Also,  I've read about having a sector free before each logical partition, is this maybe causing trouble with partition 6 and 7?

I've started up testdisk, this is the result from the scan:
```
     Partition               Start        End    Size in sectors
D FAT32                    0  32 33   783  63 48   12580864 [PRESARIO_RP]
D HPFS - NTFS            783  63 49 48154  50 17  761014265 [PRESARIO]
D HPFS - NTFS          48154  50 25 71015  78 32  367263737 [Shared]
D Linux                71015 111  9 74839 229 14   61440000
D Linux                109013  66 46 112837 184 51   61440000 [Home]
D Linux                118159  86  8 121346  99 33   51200000 [Filesystem]
D Linux Swap           121346  99 34 121601  57 40    4093936


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
```

I do belive I have found my problem.

---

### Post by krytorii on 2012-08-14
Just because some people who have the same issue may find it useful, also helps me keep track of what I've done.

After trying out testdisk and using it to "undelete" the partitions, I now have the following error from gparted: "Can't have a partition outside the disk".

Parted also gives the same error when I try and "print" inside it.

fdisk -lu now gives:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e061c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    12582911     6290432    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    12582912   773597176   380507132+   7  HPFS/NTFS
/dev/sda3       773597184  1140860920   183631868+   7  HPFS/NTFS
/dev/sda4      1140860952  1953536129   406337589    f  W95 Ext'd (LBA)
/dev/sda5      1140862976  1202302975    30720000   83  Linux
/dev/sda6      1751298048  1812738047    30720000   83  Linux
/dev/sda7      1898229760  1949429759    25600000   83  Linux
```

The extended partition is too large :roll:

---

### Post by oldfred on 2012-08-14
Swap is one of the easier partitions to delete as you do not have to backup anything. But when you create a new one you have to update the UUID in fstab or it will complain on booting and will not use the new swap until you do. 

If you have lots of RAM you may not need much swap and some use swap file rather than a partition.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by krytorii on 2012-08-15
I think it's all working now, just running bootrepair to get GRUB working again.

Used fixparts to adjust the extended partition size, I'd already  removed the swap in testdisk.

Also, somehow another home partition popped up! Probably from where I moved it before.

Thank you for all the help.

---

