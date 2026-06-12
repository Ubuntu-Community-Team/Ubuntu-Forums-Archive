---
title: "mount: wrong fs type, bad option, bad superblock on /dev/sdxyz"
date: 2010-11-18
forum: General Help
---

### Post by knomaly on 2010-11-18
Computer OS: Ubuntu 10.04
 External HDD: LaCie Rugged Hard Disk, Shock proof USB 2.0, 320 GB
 External HDD FS Format: ext4

 
When I connect the external usb drive to my computer, I get the following message:
 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,  
        missing codepage or helper program, or other error  
        In some cases useful info is found in syslog - try  
        dmesg | tail  or so  

 
 cmd $ abc@t500:~$ sudo fdisk -l /dev/sdb1  yields the following results:
  
 Disk /dev/sdb1: 320.1 GB, 320070288384 bytes 
 255 heads, 63 sectors/track, 38912 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x00000000 
  
 Disk /dev/sdb1 doesn't contain a valid partition table 


Please note that after a certain time interval (10 +/- minutes), the drive becomes inaccessible to the computer's operating system, necessitating  a reboot of the computer.
 
 Any recommendations?

---

### Post by viralmeme on 2010-11-18
> **knomaly said:**
> Disk /dev/sdb1 doesn't contain a valid partition table .. Any recommendations?

[Advanced FAT Repair]("http://www.cgsecurity.org/wiki/Advanced_FAT_Repair")

---

### Post by endotherm on 2010-11-18
what type of filesystem did you expect this disk to contain? 
fat, ntfs, ext3/4?

if it shoudl be an ext partition, try booting froma live CD or recovery mode and run:
```

sudo e2fsck -f /dev/sdb1

```

if it won;t run, then your partition is likely broken, but you may be able to recover it with TestDisk. testdisk is a data recovery program for Partitions (not for individual files) and can detect damaged/deleted partitions for recovery, as long as they are not badly overwritten.

---

### Post by knomaly on 2010-11-18
Please refer to the revised explanation of the issue in the first entry of this thread. Thanks:)

---

### Post by knomaly on 2010-11-18
[FONT=Arial][SIZE=2]Problem resolved: bad superblock. For instructions on how to recover, see article titled: "Linux: Recover Corrupted Partition From A Bad Superblock" [/SIZE][/FONT][FONT=Arial][SIZE=2]by Vivek Gite on August 15, 2008 @ [http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)[/SIZE][/FONT]

---

