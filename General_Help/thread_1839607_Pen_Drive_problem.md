---
title: "Pen Drive problem"
date: 2011-09-05
forum: General Help
---

### Post by apverma13 on 2011-09-05
hi, my computer accidently switched off while i was copying files from my 4gb Kingston Pendrive, after that it is not working. Gparted shows it as a 2Tib drive with its partition and file system unallocated and no partition table in it. I tried create partition table from gparted but it gives error. 

I tried mounting it in windows 7 too, it shows a removable disk but just after plugging it windows ask to format it but when i try to format it gives error.

---

### Post by Grenage on 2011-09-06
If you have no luck in gparted, what about fdisk?  From a terminal:

```
sudo fdisk -l
```

Is your drive listed?  If you're worried about getting the wrong drive, simply run the command both before and after plugging in the drive, and you'll see which is the pen drive.

Let's assume that the drive is sdd, and it appears to have a single partition of sdd1; once identified, you can partition and format the drive using:

```
sudo fdisk /dev/**sdd**
```

*m* will list the commands, but the ones you'll probably want are:

*p* To print the current partition table.
*d* To delete the partition.
*n* To create a new partition (you'll want a primary partition - just go with the defaults).
*t* To change the type of partition. (The type code for FAT32 is *c*).
*w* To write changes and exit.

Once that's done, you can format the partition using:

```
sudo mkdosfs -F 32 /dev/**sdd**
```

---

### Post by apverma13 on 2011-09-06
Yes the drive is listed its /dev/sdb. sudo fdisk /dev/sdb gives following :
 	Code:
 	Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xa930d706.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: The size of this disk is 2.2 TB (2199023255552 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').


Should I proceed with making a new partition?

---

### Post by Grenage on 2011-09-06
I don't know why this would happen on a read action, even with the PC crashing.  The partition table obviously just got totally trashed.

It can't hurt to overwrite the partition table - you can't physically damage the device.  Delete any existing partition (there obviously aren't any), then create a new one and write it.

---

### Post by srs5694 on 2011-09-06
It's more than a trashed partition table. fdisk is reading the drive as being 2 TiB in size. This data comes from a low-level system call that does *not* rely on any data you can write to the disk; it should be permanently hard-coded in the drive's circuitry.

My best guess is that the accidental power off resulted in a power surge or other glitch that damaged the drive's circuitry. If so, it might not be possible to recover the drive. If you've got valuable data on the drive, you could try a low-level dd copy to get everything off it, but I can't guarantee that would work.

FWIW, I have heard of this sort of thing happening before. I've never heard of a successful recovery. That's why I'm pessimistic about your chances.

---

### Post by apverma13 on 2011-09-07
I tried making a new partition but when tried to write new table on disk it gives

```

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

Error closing file

```and then pen drive is not even listed in fdisk -l

---

### Post by Grenage on 2011-09-07
> **apverma13 said:**
> I tried making a new partition but when tried to write new table on disk it gives

```

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

Error closing file

```and then pen drive is not even listed in fdisk -l

Sometimes you have to remove and reinsert the drive in Ubuntu, but that's generally only after using the eject option.

I'm going to go with srs5694 on this one and say that it's rather unlikely that you'll be able to get this drive back to a working condition - especially if you can't write a fresh partition table.

It's worth mentioning that I *have* seen a couple of drives, where their partition table was screwed and it gave out misleading volume size data, and a repartition sorted it out.

---

### Post by apverma13 on 2011-09-07
Thanks to both of you for help.

---

### Post by mastablasta on 2011-09-07
> **Grenage said:**
>  
It's worth mentioning that I *have* seen a couple of drives, where their partition table was screwed and it gave out misleading volume size data, and a repartition sorted it out.
 
 
in windows there are programmes where you can fix partition. is there nothing like that in linux? because i had similar thing happen to me on HDD in winxp and i needed to use one of those progs (i think partition doctor) to recover the partition and all the data.

---

### Post by Grenage on 2011-09-07
> **mastablasta said:**
> in windows there are programmes where you can fix partition. is there nothing like that in linux? because i had similar thing happen to me on HDD in winxp and i needed to use one of those progs (i think partition doctor) to recover the partition and all the data.

There are some great Windows recovery tools out there, but the best one I used was 'Get Data Back for NTFS'.  On linux, I hear that photorec/testdisc are good for getting data off problematic drives and recovering partition tables; I really can't imagine them being as easy as the offerings for Windows.

On Linux, with any problematic drive that *could* be recovered, I found a quick write with fdisk was sufficient.

---

### Post by srs5694 on 2011-09-07
> **Grenage said:**
> I'm going to go with srs5694 on this one and say that it's rather unlikely that you'll be able to get this drive back to a working condition - especially if you can't write a fresh partition table.

It's worth mentioning that I *have* seen a couple of drives, where their partition table was screwed and it gave out misleading volume size data, and a repartition sorted it out.

"Volume size" is a bit ambiguous. There's *disk size*, which is the size of the disk itself, as reported by the disk and returned by the BLKGETSIZE ioctl() in Linux. This value cannot be changed by writing a new partition table to the disk, since it's not stored in the partition table or anywhere on the disk.

There's also the size of individual partitions. These values *can* be altered by changing partition table data. I've seen numerous reports on these forums and elsewhere about disks that have one or more mis-sized partitions that are too big for their disks. Such problems typically occur because of bugs in partitioning software or misuse of partitioning software, and this type of problem can be fixed by adjusting the partition table data.

Linux's fdisk uses the BLKGETSIZE ioctl() to report the disk size, as returned by this line in post #3 (by apverma13):

> ```
WARNING: The size of this disk is 2.2 TB (2199023255552 bytes).
```

Since the disk is a 4 GB USB flash drive (~1/500 the size being reported), it's clear that the problem is with the total disk size, not with the size of an individual partition. I suppose there's a very slim chance that there's a Linux kernel bug that's causing it to report incorrect data on this ioctl() call, but the very first post to this thread said that Windows 7 reported an error, too, so this sounds like a drive that's got damaged firmware or control circuitry. Perhaps there's a way to fix it, but if so I don't know what it is. Given that 4 GB USB flash drives sell for as little as [$5.99 at NewEgg,](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007960%20600000468&IsNodeId=1&bop=And&Order=PRICE&PageSize=20) IMHO it's not worth expending much effort to try to recover it unless it's holding valuable data that you can't access in any other way. Of course, if somebody knows of an easy way to fix this problem, that's great; but I for one don't know of a way to fix a drive that's broken on this fundamental level. Hypothetically, such a fix would probably involve replacing the drive's firmware or perhaps even physically replacing some components.

---

### Post by Grenage on 2011-09-07
> **srs5694 said:**
> "Volume size" is a bit ambiguous. There's *disk size*, which is the size of the disk itself, as reported by the disk and returned by the BLKGETSIZE ioctl() in Linux. This value cannot be changed by writing a new partition table to the disk, since it's not stored in the partition table or anywhere on the disk.

There's also the size of individual partitions. These values *can* be altered by changing partition table data. I've seen numerous reports on these forums and elsewhere about disks that have one or more mis-sized partitions that are too big for their disks. Such problems typically occur because of bugs in partitioning software or misuse of partitioning software, and this type of problem can be fixed by adjusting the partition table data.

Linux's fdisk uses the BLKGETSIZE ioctl() to report the disk size, as returned by this line in post #3 (by apverma13):



Since the disk is a 4 GB USB flash drive (~1/500 the size being reported), it's clear that the problem is with the total disk size, not with the size of an individual partition. I suppose there's a very slim chance that there's a Linux kernel bug that's causing it to report incorrect data on this ioctl() call, but the very first post to this thread said that Windows 7 reported an error, too, so this sounds like a drive that's got damaged firmware or control circuitry. Perhaps there's a way to fix it, but if so I don't know what it is. Given that 4 GB USB flash drives sell for as little as [$5.99 at NewEgg,](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007960%20600000468&IsNodeId=1&bop=And&Order=PRICE&PageSize=20) IMHO it's not worth expending much effort to try to recover it unless it's holding valuable data that you can't access in any other way. Of course, if somebody knows of an easy way to fix this problem, that's great; but I for one don't know of a way to fix a drive that's broken on this fundamental level. Hypothetically, such a fix would probably involve replacing the drive's firmware or perhaps even physically replacing some components.

I can't recall coming across that error on fdisk before, so I wasn't really in a position to say whether or not it was rather ominouse  Since a repartition is rather quick, I figure that it never hurts to try.

Great info though, especially for someone else who comes across this thread.

---

