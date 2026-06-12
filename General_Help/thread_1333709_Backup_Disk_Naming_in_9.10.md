---
title: "Backup Disk Naming in 9.10"
date: 2009-11-21
forum: General Help
---

### Post by David Vincent-Jones on 2009-11-21
I use 'rsync' to backup my image data to a series of "Passport" removable drives.

Under previous Ubuntu versions I was always able to write the data out to '/media/drive' so it did not matter which drive I attached ... the location was always correct.

Under 9.10 it now appears that external drives are appearing only identified by their UUID. This is very unhelpful and very counter-intuitive.

Is there a work-around?

---

### Post by dcstar on 2009-11-21
> **David Vincent-Jones said:**
> I use 'rsync' to backup my image data to a series of "Passport" removable drives.

Under previous Ubuntu versions I was always able to write the data out to '/media/drive' so it did not matter which drive I attached ... the location was always correct.

Under 9.10 it now appears that external drives are appearing only identified by their UUID. This is very unhelpful and very counter-intuitive.

Is there a work-around?

As has been stated many times, put a label on the partitions and they will always be mounted under that label.

---

### Post by louieb on 2009-11-21
One way is to give each backup file system a label, then it will be mounted in /media/<label>.  Just give each file system the same label. 

Can use Gparted or e2label.

[IMG]http://louboldt.com/ptwocents.gif[/IMG] I can see the logic of mounting by UUID. Using it keep each file system unique,  and guarantees that a given file system will always be mounted with the same name. 

Wonder what it would do if you plugged in two drives with the same label?

opps guess I was daydreaming. see you already got the same answer.

---

### Post by David Vincent-Jones on 2009-11-22
As far as I can see, in order to add a specific label to the backup drive I need to reformat and start from scratch ... is that correct.

Why is there such a change from 9.04 to 9.10? I had no problem on earlier versions.

---

### Post by louieb on 2009-11-22
Not! Sound like you confused disk label which is another name for the partition table, with the label on a partition.

Right click on the partition - select label from the drop down list.  You want to add a partition label - not a disk label. 

> Why is there such a change from 9.04 to 9.10? 

Don't know what change your wondering about.  But disk labels and partition labels have been and worked the same since before I started using Linux in 2006.

---

### Post by David Vincent-Jones on 2009-11-22
When I right click on the backup-disk the option for adding a label is greyed out ... I assume on account of there only being a single NTFS file space and no defined partitions.
Creating a partition will of course wipe out everything on the disk ... unless there is another way.

---

### Post by louieb on 2009-11-22
Sorry  - not familiar - how do you mount or put data on a hdd without at least one partition.  Just out of curiosity can you post a screen shot of the Gparted window?     

or list the partition table 
```
sudo fdisk -l
```

---

### Post by David Vincent-Jones on 2009-11-22
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

This is a standard 'Passport' Western Digital USB drive. I have 3 of them that I rotate for backup purposes.

I am not sure why I would need to put partitions into any of the backup drives ... they are simply storage areas for the incremental compressed files.

---

### Post by dcstar on 2009-11-22
> **David Vincent-Jones said:**
> Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1**               1       38913   312568641    7  **HPFS/NTFS**

This is a standard 'Passport' Western Digital USB drive. I have 3 of them that I rotate for backup purposes.

I am not sure why I would need to put partitions into any of the backup drives ... they are simply storage areas for the incremental compressed files.

They already **have** partitions - you cannot do anything without a partition.

---

### Post by louieb on 2009-11-22
Thanks for the fdisk listing. And yes the the line in red is a partition. It takes up the whole hdd. 

If the label option is grayed out. In the same right click menu there is the **unmount **option click on it to **unmount** the partition. Then you should be able to click the** label **option.   
```

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sdb1               1       38913   312568641    7  HPFS/NTFS[/COLOR]

```> I am not sure why I would need to put partitions into any of the backup drives ...Thats a question for Bill Gates and IBM - Hard drives in PCs have been organized with the ms-dos partition table since the 1st IBM PC came out. Can't recall when that was,  I got my 1st in 1986. Had a 20MB hard drive. It used the same partition table that you see today.

---

