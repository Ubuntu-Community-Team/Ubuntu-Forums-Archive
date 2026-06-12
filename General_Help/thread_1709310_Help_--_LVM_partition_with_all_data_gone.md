---
title: "Help -- LVM partition with all data gone"
date: 2011-03-18
forum: General Help
---

### Post by itsmarik on 2011-03-18
Hello -- I'm new to this forum, so please forgive me if I'm posting in the wrong place or not explaining things well.
 

 I have LVM sitting on top of linux software raid, and somehow I manage to loose an entire LVM partition (I think).  Everything was working fine, until I rebooted.
 

 This is my current setup:
 

 4 disks in software raid10.  The raid starts fine and mdstat reports no problems.
 I've created an LVM group called MM on top of raid10, using entire disk space.  There is only one PV and one LV, also using full disk capacity.  The LV name is Disk0.  There was a device for Disk0 created under:  /dev/mapper/MM-Disk0 for this LV.  Before rebooting, there was also a device for partition 1 created as:  /dev/mapper/MM-Disk0p1, but after reboot, that file disappeared.
 

 When I run parted on MM-Disk0, it shows GUID partition table, and a single partition with ext4 fs.  This is consistent with the way I initially set this up.  When I open up Disk Utility gui, it shows the GUID table, but it is unable to recognize any partitions.  Running fdisk also shows 1 partition as being created, even though it says it does not support GPT.
 

 So I guess my questions are, what happened?  And is it possible to recover MM-Disk0p1 device?


If anyone can offer any help, I would greatly appreciate it.


Thanks!

---

### Post by srs5694 on 2011-03-18
Partitioning a logical volume is pointless at best. The whole point of LVM is to *replace* inflexible partitions with a much more flexible container for filesystems (although paradoxically LVM is usually implemented *on top of* regular partitions). That is, once you've created your volume group, you can create as many logical volumes as you like to hold your filesystems and swap -- for instance, one for root (/), one for /home, and one for swap. If you subsequently add disks to the LVM, you can then expand one or more of these logical volumes pretty seamlessly; or if you want to try a new distribution, you can create a new logical volume for it (perhaps shrinking one of the existing ones first) without the dangers inherent in moving partitions, and with less risk than some types of partition resizing operations.

Putting a partition table in a logical volume is rather like buying a minivan for transportation and then strapping a subcompact car to its roof and rigging it so you can drive the minivan from the subcompact's driver's seat. It might work, but it's ungainly and dangerous. You'd be better off with either the minivan alone or the subcompact alone.

If you've just set this up and have no data on the drive, I suggest you delete your single logical volume, create whatever logical volume(s) you need to store your data, and create filesystems on those logical volumes.

If you've actually stored data in the partitions inside your logical volume, you'll need to do some data recovery. Quite honestly, I'm not sure how you'd go about this, since AFAIK that type of setup isn't supported, and I don't know what tools will create the device nodes you require. Probably there's some way to get udev to do it, but I'm not positive of that. You could also try typing "sudo partprobe" or "sudo partprobe /dev/MM-Disk0" and see if that makes the device node appear. Another approach you could try is to boot as many different rescue CDs as you can find -- the Ubuntu "alternate" installation CD/DVD (IIRC, the desktop installer lacks RAID and LVM support), [System Rescue CD](http://www.sysresccd.org), [Parted Magic](http://partedmagic.com), [Knoppix](http://knoppix.com), etc. Once booted, check each one for device nodes that might refer to that partition you created. If you find it, back up the data and then proceed to reconfigure the system as I've just outlined.

If that fails, it's conceivable that [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) will be able to convert your single partition-within-LVM-within-RAID into a partition-within-RAID. You'd definitely have to delete the LVM data to get this to work. (It's conceivable that TestDisk would do this when it writes the new partition table, but I don't know enough about low-level LVM data structures to know if writing a partition table over the RAID device would overwrite the LVM signatures.) To try this, you'd need to point TestDisk directly at the RAID device (/dev/md0). This approach seems risky to me, but I don't know how risky because I don't know enough about the low-level LVM data structures or what the LVM utilities do when deleting LVM data structures. I present it only as an option of desperation, and with the caveat that you might end up making matters worse if you try it.

A final point: The [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) that you apparently used on your logical volume includes what's known as a *protective MBR*, which is a [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) partition table that contains a single bogus partition that spans the entire disk. The protective MBR is intended to keep GPT-unaware utilities, such as Linux fdisk, from modifying the disk. It's that protective partition that fdisk is showing you. That partition is *not* the GPT partition you actually created inside the logical volume. If you wanted to modify the GPT partition, you'd need to use a tool such as gdisk, parted, or GParted. I'm presenting this information just to be complete; I don't think that editing the GPT partitions will do you any good.

---

### Post by psusi on 2011-03-18
Heh!  I love that analogy.  Brilliant!

---

### Post by itsmarik on 2011-03-18
Thanks for the quick reply.

I actually didn't realize that you could put a filesystem on a logical  volume directly, which is why I partitioned it in the first place.   Placing fs directly seems way better than what I did.  I guess I'll be  changing things around a bit.

Anyway, I do have data which I'd prefer to preserve.  I'm doing dd on  entire LVM device to a second disk right now.  Once that's done, I'm  going to try a few things with the second disk to see if I can recover  the data.  I've been googling around a bit and it looks like a bad  superblock could cause similar issues, although not LVM related.  But  since my LVM is set up more like a traditional partition, maybe it would  help.  Also, I've noticed in the past that if you create and format a  partition (say, an ext4), put some data on it, then delete it, and then  recreate it using the same exact sector boundaries, the filesystem and  all data on it would be preserved.  I found that to be both odd and  cool.  I'll give that a shot too.

I actually tried using parted also, and it recognized a GPT table and  showed an ext4 partition as being there.  GParted, on the other hand,  says it does not support LVMs.

Thanks again for the replies.  Sorry to be so dumb with this.  I've been  mostly using linux as a desktop user for a while, and for the most  part, things simply worked w/o problems, so there wasn't much need in  learning more technical and troubleshooting stuff.

---

### Post by srs5694 on 2011-03-18
> **itsmarik said:**
> Anyway, I do have data which I'd prefer to preserve.  I'm doing dd on  entire LVM device to a second disk right now.

I didn't realize you had another disk big enough to use for this purpose; for most people with RAID arrays, that's not the case. In any event, to simplify recovery, you should be able to do a dd copy from the logical volume to the other disk, as in:

```

sudo dd if=/dev/mapper/MM-Disk0 of=/dev/sdc

```

Change /dev/sdc as appropriate, of course. Assuming /dev/sdc is big enough, it will then hold the partition table and partitions you put on the logical volume. You might need to type "sudo partprobe" or reboot to get the kernel to recognize the partitions, though. Also, the way GPT works, there's a chance that the kernel won't recognize the partitions until you move the backup GPT data to the end of the disk. You can do that with the sgdisk program from the [GPT fdisk (gdisk/sgdisk)](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.0/gdisk-binaries/) package:

```

sudo sgdisk -e /dev/sdc

```

I don't think that will be necessary, but it might be.

> Also, I've noticed in the past that if you create and format a  partition (say, an ext4), put some data on it, then delete it, and then  recreate it using the same exact sector boundaries, the filesystem and  all data on it would be preserved.  I found that to be both odd and  cool.  I'll give that a shot too.

Yup. That's the principle that TestDisk uses to recover partitions; it looks for filesystems' identifying data, then builds partitions around anything it finds.

---

### Post by itsmarik on 2011-03-18
Actually, I have an external raid enclosure with two 2TB drives in raid0.  That thing is big enough to hold everything and that's where I'm cloning to.

---

### Post by itsmarik on 2011-03-20
OK.  Problem seems to have been solved now.  After cloning the LVM partition to the external raid, I rebooted the system, and it looks like the filesystem on a "cloned" drive fixed itself.  I was able to mount it and all the data was there.

LVM is still not mountable, but that doesn't matter, since I'm going to redo it the way srs5694 suggested.  I guess LVM really doesn't like being partitioned the way I did it.

Thanks a lot for all your help srs5694!

---

