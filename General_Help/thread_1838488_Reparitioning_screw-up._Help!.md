---
title: "Reparitioning screw-up. Help!"
date: 2011-09-03
forum: General Help
---

### Post by BungaDunga on 2011-09-03
EDIT: RePARTITIONing. Dammit, fingers!

I have an external hard drive with 3 partitions, two of which are old Windows installs from when it was an internal hard drive, and one is a bigger partition with data on it. Important, un-backed-up data, of course.

I decided to remove the Windows partitions and resize the big partition to make some room. I deleted one of the partitions and told GParted to resize the data partition into the space to the left. 

I left it over night and saw, staring at me, this:
[IMG]http://i.imgur.com/eaQ68.png[/IMG]

It reports:

```
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name    : /dev/sdd3
NTFS volume version: 3.1
Cluster size    : 4096 bytes
Current volume size: 261728571904 bytes (261729 MB)
Current device size: 261728409600 bytes (261729 MB)
ERROR: Current NTFS volume size is bigger than the
device size!
Corrupt partition table or incorrect device partitioning?

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
```

I poked around in TestDisk briefly (which I've used to successfully recover partition tables in other situations, and PhotoRec to pull the files out when that hasn't worked) and it reports this:

```

Disk /dev/sdd - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33  2889 254 63   46425802
Error: size boot_sector 511188619 > partition 511188300
Invalid NTFS or EXFAT boot
 3 P HPFS - NTFS           7093   0  1 38912 254 63  511188300
 3 P HPFS - NTFS           7093   0  1 38912 254 63  511188300

```

"Quick search" shows:
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdd - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
L HPFS - NTFS              0  32 33  2889 254 63   46425802
* HPFS - NTFS           2890   0  1 34710 254 63  511204365

```

And then
```
Disk /dev/sdd - 320 GB / 298 GiB - CHS 38914 255 63

     Partition                  Start        End    Size in sectors

 1 E extended LBA             0  32  1  2889 254 63   46425834
 2 * HPFS - NTFS           2890   0  1 34710 254 63  511204365
 5 L HPFS - NTFS              0  32 33  2889 254 63   46425802

```

I'm not sure how serious this is. What's the best course of action now?

---

### Post by Rob_H on 2011-09-03
I think you're about to experience a life lesson.

---

### Post by BungaDunga on 2011-09-03
> **Rob_H said:**
> I think you're about to experience a life lesson.

I'd appreciate help with learning

a) what exactly went wrong,
b) why it went wrong,
c) what shape my data is in, and
d) what I should do that can recover data without making it worse

---

### Post by JC Cheloven on 2011-09-03
> **Rob_H said:**
> I think you're about to experience a life lesson.I'd say this doesn't help a lot the OP.

@Bunga: NTFS is a windows filesystem. All your partitions are (were) ntfs, so first thing to try out would be to plug you disk under windows and see what it can do about it.
Hope this helps. Having tried testdisk without success is not a good sympthom though.

---

### Post by BungaDunga on 2011-09-03
> **JC Cheloven said:**
> I'd say this doesn't help a lot the OP.

@Bunga: NTFS is a windows filesystem. All your partitions are (were) ntfs, so first thing to try out would be to plug you disk under windows and see what it can do about it.
Hope this helps. Having tried testdisk without success is not a good sympthom though.

Windows sees an unformatted, unlabeled partition in the same place as GParted sees the Data partition. I looked at it with diskpart and Windows Explorer; I'm not sure what other tools there are on Windows for diagnosis.

Also, I don't really know how to interpret what testdisk or ntfsresize is saying. Something went wrong while repartitioning, but at what point? Did it start moving my data around and then fail? Is all my data where it was, but the partition table's scrambled? Is my data scrambled? How can I work out what is actually physically on the disk?

Also, I get this when it tries to mount:
```
Error mounting: mount exited with exit code 12: Failed to read last sector (511188618): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdd3': Invalid argument
The device '/dev/sdd3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

---

### Post by JC Cheloven on 2011-09-04
> **BungaDunga said:**
> (...)
Windows sees an unformatted, unlabeled partition in the same place as GParted sees the Data partition. I looked at it with diskpart and Windows Explorer; I'm not sure what other tools there are on Windows for diagnosis. Sorry to hear that. I had a marginal hope of your partition table being in a workable state from within windows. Seems not to be the case.

> 
Something went wrong while repartitioning, but at what point? Did it start moving my data around and then fail? Is all my data where it was, but the partition table's scrambled? Is my data scrambled? How can I work out what is actually physically on the disk?
The information you ask for could have helped *before* starting playing around with partitions. I'm afraid it will be of little help in the present state of your disk. But it can serve you for the future. Basically:
[LIST]
[*]- Playing around with partitions is **always** risky. No matter from which OS or using which tools.
[*]- The ntfs filesystem is prone to fragmentation. As a minimal safety rule, you should defragment the filesystem before facing any partition task (defragment is to be done from windows). Such task often involves moving data, and the more the fragmentation, the more the risk. 
[*]- The operation you attempted in particular, involved moving a lot of data. This is both slow, and again risky when done during a partition modification. My personal advice would have been by all means to take all your data to another media first. Once your data is safe, delete the data from your disk, and proceed with the repartition  (which will be way faster and safer without any data to move). But it's late for that advice.
[*]- Gparted probably spent some of the night moving data. So probably an unkown portion of your data has been moved already. Also probably some other unkown portion of your data has overwritten an equivalent portion of your data located in a different place. To sum up, most likely your data is chopped over there.
[*]- In the meanwhile, your partition table got corrupted (for one or other reason), so your data is spread in an almost impossible to investigate  way. [/LIST]

Let's go now with what could be of help (this is a help forum after all, isn't it?). 

[LIST]
[*]- If my picture above is true, your best option is trying to recover individual files using tools like photorec or recoverjpeg. 
[*]- Nevertheless, before that, the program testdisk is supposed to offer you menu driven options to (try to) recover your partitions. Did it? Please read about it if you're unfamiliar with it. For example [here]("http://www.howtoforge.com/data_recovery_with_testdisk") or in the manpages, google, etc.
[*]- See what you can make from [this]("https://help.ubuntu.com/community/DataRecovery"). It's the customary reference over here.
[/LIST]
Best of luck. The situation is complicated though.
JC

---

### Post by oldfred on 2011-09-04
All NTFS partitions have to have a valid partition boot sector - PBR. Test disk can restore a basic one and chkdsk from Windows can often run repairs. But if partition was not correctly moved left and PBR updated it may have other internal issues.

I generally prefer not to move partitions left, as it has to copy & verify all data and with NTFS update PBR. Any interruption, power failure or other issue can then corrupt data.

---

### Post by BungaDunga on 2011-09-05
So, good news, I fixed it. I'll reproduce the advice I received that did it here:

> So here's what I think has happened:

This part is informed guesswork: to extend an NTFS partition leftward, I would expect gparted to do the following: (a) resize the NTFS filesytem to its smallest possible size, thereby consolidating all its blocks at the beginning of its partition (b) alter the partition table to make the partition cover the formerly unoccupied space to the left, thereby causing the shrunken NTFS filesystem to appear at an offset within the partition (c) copy the filesystem blocks from that offset to offset 0, starting at the left so that blocks that get overwritten have already been copied by the time the overwrite happens (d) resize the NTFS filesystem to fill the new partition.

It looks to me as if gparted didn't get as far as (b) because it failed at (a). If that's right, it's good because it means that the potentially very destructive (c) will not have happened.

So why would (a) fail, and can the result be fixed?

There's an unallocated block of 1MiB at the start of the disk, which says to me that it was originally set up by Windows Vista or Windows 7. The partitioner that comes with these systems pays no attention to the old conventions about making partitions start on "track" boundaries and end on "cylinder" boundaries, on the perfectly reasonable grounds that (a) the head and sector counts are completely meaningless on modern drives and (b) as more drives become available with internal 4KiB sectoring, forcing partitions to start on a non-4KiB boundary is totally counterproductive. Instead, Vista/7 starts partitions on 1MiB boundaries and gives them whole-MiB sizes.

The Linux kernel, unless told otherwise, will assume a disk geometry of 63 sectors per track and 255 heads. This gives rise to a logical cylinder size of 63 * 255 * 512 bytes = 8225280 bytes, which is not a multiple of 1MiB (1048576 bytes). Using command-line Linux partitioning tools against Vista-formatted drives, you'll frequently see warnings about partitions not ending on cylinder boundaries.

I suspect that gparted has silently "fixed" those "errors", and that as a result, /dev/sdd3 is now a little smaller than Vista/7 left it.

The reported device size (261728409600 bytes) is exactly 31820 * 8225280 bytes, but it's not an exact muliple of 1MiB. If we round it up to the next such multiple, we get 261728763904 bytes.

The reported filesystem size (261728571904 bytes) is 162304 bytes bigger than the partition's present size, but 192000 bytes smaller than the rounded-up size. So I'm thinking that all that will need doing is fixing the partition size to make it a multiple of 1MiB again, and the filesystem should become accessible again as long as no data recovery tool has "fixed" it too much.

The steps I'd use to do that (after making a ddrescue backup, naturally!) are:

1. Use sfdisk --dump /dev/sdd >sdd.parts.old to get an editable version of the present partition table.

2. Edit sdd.parts.old, round up all the partition sizes to the next multiple of 2048 (because 2048 512-byte sectors is 1MiB) and save it as sdd.parts.new.

3. Use sfdisk -S 32 -H 64 -n /dev/sdd <sdd.parts.new to do a dummy run at applying the edited partition table to the disk. Setting sectors per track to 32 and heads to 64 yields a logical cylinder size of 1MiB and keeps both Linux and Windows happy.

4. If the dummy run reported no errors, sfdisk -S 32 -H 64 /dev/sdd <sdd.parts.new to apply the new partitioning and sfdisk --re-read to ask the kernel to adopt it.


---

### Post by JC Cheloven on 2011-09-06
Awesome, people knows about a wonderful variety of things over there :)

Hope you learned the most important lesson from this: Always have a backup of your data! 

Cheers
JC

---

