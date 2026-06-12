---
title: "jbd2/sda1 making hard drives spin up."
date: 2010-08-07
forum: General Help
---

### Post by markp1989 on 2010-08-07
im my file server, i like keeping the hard drives spandown as much as possible to save power usage, as the data drives can normaly go for hours without being accessed.

i have set hdparm to send the drives to sleep 10min after there is no access.

only problem im having is that jbd2/sda1-7  which appears to be part of ext4s journaling spins up all my hard drives within 2 min of them spinning down.

if the data on the drive hasnt changed surley there is no reason for the journal to be updated?

thanks for any help. mark

---

### Post by markp1989 on 2010-09-02
ok, i have since changed the layout of the drives in my mediapc/server. im now using a ssd for root and home partitions and 2 1.5tb hard drives for data.

, but im still having trouble getting the 2 data drives to spin down, and stay that way. 

surley they dont need 2 be on all the time, nothing is accessing them? 

I have tried hdparm -S120 (10min) on both the drives that i want to be sleeping 90% of the time, but im still having no luck, they never seem to spin down on there own, and if i manualy spin them down, they wake up in a bout 5 sec.

im still seing the jbd2 process in iotop alot, what need is there to update the journal (if thats what it is) of the 2 data drives, if no data has changed. 

thanks for any pointers :)

---

### Post by dargaud on 2010-09-23
Have you solved this ? I'd be interested in a solution, being in the same situation.

---

### Post by markp1989 on 2010-10-06
> **dargaud said:**
> Have you solved this ? I'd be interested in a solution, being in the same situation.

Still had no luck, if you find something, let me know :) 

if i find anything, I will post it here .

---

### Post by cullis on 2010-11-05
I am having a similar problem. I have two 2TB drives mirrored with an EXT3 file system and they spin down fine. I also have two 1TB drives mirrored with an EXT4 filesystem and I can't get them to spindown. When I try to see what is accessing the drive the main process appears to be Jbd2/dm-0-8.

My OS is running off a separate SD card.

Anyone have any ideas? Is there a utility/tool that can show me exactly what is accessing the disks?

---

### Post by dcstar on 2010-11-05
> **cullis said:**
> I am having a similar problem. I have two 2TB drives mirrored with an EXT3 file system and they spin down fine. I also have two 1TB drives mirrored with an EXT4 filesystem and I can't get them to spindown. When I try to see what is accessing the drive the main process appears to be Jbd2/dm-0-8.

My OS is running off a separate SD card.

Anyone have any ideas? Is there a utility/tool that can show me exactly what is accessing the disks?

```
man atsar
```
[http://www.sarcheck.com/sclinux.htm](http://www.sarcheck.com/sclinux.htm)

---

### Post by dcstar on 2010-11-05
> **markp1989 said:**
> 
.........
only problem im having is that jbd2/sda1-7  which appears to be part of ext4s journaling spins up all my hard drives within 2 min of them spinning down.

if the data on the drive hasnt changed surley there is no reason for the journal to be updated?

thanks for any help. mark

AFAIK the kernel syncs all mounted filesystems on a regular cycle, and various other processes will be checking all mounted filesystems to ensure that they are still available.

If you do not mount your filesystems with the **noatime** option then every time a read access is done (even from cached data) a timestamp change will be written to whatever is read - which will force a physical disk write whenever the next sync cycle arrives.

---

### Post by romain145 on 2010-11-20
+1.

I'm using an ubuntu 10.10 laptop, and having same troubles with jbd2. 
In fstab I mounted / as noatime. I even tried ext2 (instead of ext4, thinking jbd2 should be useless) but the problem is still here.
The had disk drive cannot stay in sleep longer than 20sec...

It's really annoying... I'm looking for a way (even an aufs solution) to avoid this disk spinning up at any time.

Any idea developpers teams ?

---

### Post by ahnise on 2010-11-22
I am having the same issue Ubuntu 10.10 with laptop mode tools installed. Using laptop mode tools to remount noatime bi still seeing the disk access. I can go for about 1.5 min at the longest.

---

