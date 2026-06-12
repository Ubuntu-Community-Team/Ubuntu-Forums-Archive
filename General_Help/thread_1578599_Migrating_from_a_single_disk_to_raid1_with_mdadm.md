---
title: "Migrating from a single disk to raid1 with mdadm"
date: 2010-09-20
forum: General Help
---

### Post by n9jdz on 2010-09-20
I have a question about moving a system from a single hard drive with a few partitions with ext3 to two drives in a raid1 setup. 
In the past I have setup new disks with mdadm and copied the data from old disk to new raid. Worked great. I need to reduce the down time to do this on system someone setup.

My idea is something like the following:

Install the old disk on a system with an identical, empty, disk.
Use a rescue CD to boot the system.
Use fdisk to change the partitions from type 83 to fd for each of the linux partitions.
On the empty drive, make partitions to match the ones on the old disk.
For each of the partitions on the old drive do the following:
	mdadm –create /dev/mdX –level=1 –raid-devices=2 /dev/hdaX missing
	where mdX is an unused device and hdaX is the disk partition.

Wait until the raids are stable by looking at /proc/mdstat
When the raids are stable, do the following for each of the new mdX devices.
	mdadm –add /dev/mdX /dev/hdbX
	where mdX and hdbX match the raid created with hdaX

Wait until the raids are stable by looking at /proc/mdstat
Mount the partition containing /etc and edit fstab to reflect the change from hdaX to mdX
Redo GRUB and a few other things.



I did a quick test with two spare drives with a simple install and an ext3 filesystem. It seems to work.

Does anyone know of any problems this may cause, data corruption and such?

Thanks

---

### Post by frostschutz on 2010-09-20
You can't simply softraid a partition that already has a filesystem on it, because the raid itself will require some space for its superblock / metadata, which would overwrite part of the already present filesystem.

What you'll have to do is partition the new disk as raid, and for each partition create a raid layer on the new disk with a slot for the old disk missing; then mkfs the raid devices, and copy your data over from the old disk onto the raid.

At that point you'll still have your data intact on the old disk, and a copy of the data on the new disk in raid format.

Once you've double checked that the copy is good, you can kill the old disk and follow standard procedure - as if the old disk failed and gets replaced with a new one, you can clone the partition table, and add it with mdadm. The raid will then sync and you'll have your data on both disks, this time as RAID.

All that's left then is make it bootable, i.e. you'll have to edit your fstab, mdadm.conf, update kernel and initramfs, and install grub on both disks.

EDIT: I think that's what you were describing in your first sentence actually; there is no shorter way, unless your filesystems allow easy shrinking. You could shrink the filesystem, then mdadm the partition (raid superblock version 0.9 will be located at the end of the partition, which is then no longer occupied by the shrunk filesystem), then grow the filesystem on the raid device; and then add the new disk to the raid.

However that's a dangerous operation, I think it's better to stick to the method you know works fine.

Without shrinking, you'd have to fsck the filesystem on the raid device, and hope that fsck is smart enough to cope with the partition suddenly becoming a bit smaller since the space occupied by the raid is missing... most filesystems do not like that at all.

---

### Post by n9jdz on 2010-09-21
Thanks for the reply.
That's sort of what I expected. This morning we filled the test drive to 100% with dummy data. At that point the raid started throwing errors.

The resizing would seem to be a chore in itself. I would need to do tune2fs -O, e2fsck -f, resize2fs, fdisk and tune2fs -j hoping I don't make a mistake in all that.

We have now decided to simply buy a new system, set it up properly and rsync the data. At some point we shut down the old server and change the IP of the new one.

Thanks again.

---

