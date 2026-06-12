---
title: "RAID 1 File Recovery - MyBook World Edition"
date: 2011-04-18
forum: General Help
---

### Post by Tnwagn on 2011-04-18
I have a 2TB MyBook World Edition II system that was recently corrupted when a power outage knocked the device out of commission. I can still power up the unit, and access it over my network. I can login and even check on the status of the drives, which according to the system are OK. However, the RAID volume itself became corrupted when it was knocked offline during the outage.

As such, I've begun to try and figure out how to recover the files I have on the system. I tried everything I could keeping the drives inside the box but that has gotten me nowhere so I have resorted to pulling a drive from the unit and seeing what I can do from there. The system was setup in RAID 1, so it would seem there wouldn't be any jumping through hoops to access the files that are stored on the drive.

My first search returned this site

[http://randomlylearned.blogspot.com/2008/09/recover-data-from-my-book-world-edition.html](http://randomlylearned.blogspot.com/2008/09/recover-data-from-my-book-world-edition.html)

Following this, I was able to mount the drive but was unable to access any of the files.

So, with a bit more searching I came across these two guides which state that the data is stored on an XFS partition.

[http://ifnothingelseworks.com/hardware/recovering-files-from-a-my-book-world-edition/](http://ifnothingelseworks.com/hardware/recovering-files-from-a-my-book-world-edition/)

[http://ubuntuforums.org/showthread.php?t=1645431](http://ubuntuforums.org/showthread.php?t=1645431)

Based on those two guides, it should be no problem to mount the partition from the drive as an XFS partition and get to the files.

However, this is where things really get interesting. Searching for the drive's partition number with Fdisk I returned 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't 

support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976762583+  ee  GPT

```So, using parted on sdd I returned

```
Model: WDC WD10 EARS-00MVWB0 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      32.9MB  2040MB  2007MB  ext3            primary  raid
 2      2040MB  2303MB  263MB   linux-swap(v1)  primary  raid
 3      2303MB  3315MB  1012MB  ext3            primary  raid
 4      3315MB  1000GB  997GB                   primary  raid
```Hmmmmmmmmm, so the partition where the data is stored is listed by GNU as having no filesystem.

I attempt to mount the partition anyway just to see if there is any luck....

```
ubuntu@ubuntu:~$ sudo mount -t xfs -o ro /dev/sdd4 /media/hope
mount: wrong fs type, bad option, bad superblock on /dev/sdd4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```No luck.

So, after more poking around I came across this,

[http://en.wikipedia.org/wiki/Western_Digital_My_Book#Internals](http://en.wikipedia.org/wiki/Western_Digital_My_Book#Internals)

Suggesting I try to use mdadm to mount the drive through software RAID. I attempted

```
sudo apt-get install mdadm
```But was thrown errors.



All in all, I am at a standstill. I am pretty limited in my knowledge of Linux and I'm really just following what others have done. Given the amount of data I've collected on the issue, I feel like one of you all who have a much deeper knowledge of Linux and these issues will be able to help me take the next step in getting to access these files. So, any help would be appreciated and let me know if there is any other information that would help in the process. Thanks ahead of time.

---

### Post by Tnwagn on 2011-04-25
I poked around a bit more with this over the weekend. First post aside, it really boils down to the fact that I would be able to see the files if I could mount the last partition of the disk. However, as GNU parted doesn't recognize the file system of the partition I'm really at a standstill. Could testdisk possibly be used to recover set the file system for the partition?

---

### Post by Mylorharbour on 2012-04-12
Ohh..........It's a real shame this thread wasn't marked solved because I've had preciseley the same issue with my Mybook drives (raid) for months now. Does anyone know whether this is fixable?

I've tried a PM to the original poster but it appears they haven't been on the forum for a year so they're not likely to get it.

---

### Post by leecook on 2012-08-05
And I have the same issue too. Did you have any luck?

---

