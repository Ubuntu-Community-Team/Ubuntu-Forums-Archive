---
title: "Logical partitions within software RAID?"
date: 2010-10-04
forum: General Help
---

### Post by BrutalSpoon on 2010-10-04
Hi everyone,

So, over the next couple of days I'm going to be building a new file server based on Ubuntu with three 2TB drives (and possibly a pair of 500GB drives I already own) in RAID 5 using mdadm.

Firstly, I'm under the impression that I *would* be able to add the 500GB drives using mdadm; while all drives need to be of the same capacity for hardware RAIDs, software RAIDs are able to work with different-sized volumes. Is this correct?

Secondly, and the main question for this thread, am I right in thinking that mdadm presents the RAID as a drive which can then be used like a single drive would be?

I'm hoping to create a logical partition within the RAID formatted with HFS+ which can be used for network-based Time Machine backups for a few Macs in my house.

Now, this is where I particularly show my ignorant side: is it possible to create a logical partition with a variable size? Similar to how a virtual hard drive works with some virtual machines; a "drive" may take up to 200GB, for example, but is only as large as the amount of data it stores. If it is possible, is this only for certain partition formats?

I realise that these questions may seem a little stupid, but I'd just like to get an idea of how much I'll be able to achieve with a software RAID other than a single partition for basic file storage.

Thanks in advance, as always,
BrutalSpoon.

---

### Post by yota on 2010-10-04
> **BrutalSpoon said:**
> Hi everyone,
Firstly, I'm under the impression that I *would* be able to add the 500GB drives using mdadm; while all drives need to be of the same capacity for hardware RAIDs, software RAIDs are able to work with different-sized volumes. Is this correct?

Software RAID will work with different sized drives, but you'll still need to create same-sized linux raid partitions on them.

> **BrutalSpoon said:**
> 
Secondly, and the main question for this thread, am I right in thinking that mdadm presents the RAID as a drive which can then be used like a single drive would be?

Not exactly: the RAID drive (i.e. /dev/md0) will look like a partition on which you have to make a filesystem.
I you want do get different partitions you need to make them on the original drives and assemble them in two groups obtaining /dev/md0 and /dev/md1 (and so on...)

To further explain something like this:
sda1+sdb1+sdc1=md0
sda2+sdb2+sdc2=md1
sda3 (spare space if sda is bigger than sdb and sdc) 

> **BrutalSpoon said:**
> 
Now, this is where I particularly show my ignorant side: is it possible to create a logical partition with a variable size? Similar to how a virtual hard drive works with some virtual machines; a "drive" may take up to 200GB, for example, but is only as large as the amount of data it stores. If it is possible, is this only for certain partition formats?

Maybe you need [LVM]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)") (with it's builtin raid 1 or eventually on top of mdadm RAID5), but beware! Often making complex baroque disks layout at home might eventually endup in doing more harm than good.

Experiment a bit with a virtual machine (virtual discs are really inexpensive ;-) ) before choosing which solution is the best for you.

p.s. I forgot: since you are talking of "network based backups" are you sure that you need the underlying filesystem to be HFS+? Maybe any filesystem will do as long as you export it on a way suitable for the purpose...

---

### Post by BrutalSpoon on 2010-10-04
> **yota said:**
> Software RAID will work with different sized drives, but you'll still need to create same-sized linux raid partitions on them.

So does that mean that if I wanted to use the 2TB drives and the 500GB drives I'd have to split each 2TB drives into four 500GB partitions? I guess that completely negates the point of the RAID because if one drive were to fail I'd lose the whole RAID, right?

> **yota said:**
> Not exactly: the RAID drive (i.e. /dev/md0) will look like a partition on which you have to make a filesystem.
I you want do get different partitions you need to make them on the original drives and assemble them in two groups obtaining /dev/md0 and /dev/md1 (and so on...)

To further explain something like this:
sda1+sdb1+sdc1=md0
sda2+sdb2+sdc2=md1
sda3 (spare space if sda is bigger than sdb and sdc) 


So you're saying that there's no way to have multiple partitions within a software RAID, and that if I want multiple RAID'd partitions I'd need to have multiple software RAIDs. Is that right?


> **yota said:**
> Maybe you need [LVM]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)") (with it's builtin raid 1 or eventually on top of mdadm RAID5), but beware! Often making complex baroque disks layout at home might eventually endup in doing more harm than good.

Experiment a bit with a virtual machine (virtual discs are really inexpensive ;-) ) before choosing which solution is the best for you.

This is starting to get a bit abstract for me :P So I'd potentially be creating a single logical volume using mdadm which would appear as a physical volume in LVM which I could then potentially use to split into multiple logical volumes managed by LVM?

> **yota said:**
> p.s. I forgot: since you are talking of "network based backups" are you sure that you need the underlying filesystem to be HFS+? Maybe any filesystem will do as long as you export it on a way suitable for the purpose...

Ah, thanks for pointing that out. I was always under the impression that you needed to have a partition specifically for Time Machine and that it needed to be formatted as HFS+.

That got me doing a bit of extra reading, and it turns out that I skimmed over some pages which I read before about setting up a Time Machine server on Ubuntu. It looks like as Time Machine will happily back up onto ext3 or NTFS *provided that netatalk is correctly configured*. That certainly makes things a hell of a lot simpler. Looks like I will be using a simple single partitioned RAID, after all.

My question about needing to split the 2TB drives into multiple partitions if I want to use the 500GB drives in the RAID still stands, though.

Thank you so much for the help!

---

### Post by psusi on 2010-10-04
> **BrutalSpoon said:**
> 
This is starting to get a bit abstract for me :P So I'd potentially be creating a single logical volume using mdadm which would appear as a physical volume in LVM which I could then potentially use to split into multiple logical volumes managed by LVM?

That's the gist of it, yes.  The nice thing about lvm is that you can create new volumes or expand existing ones any time you want, as long as you still have free space.  That sounds like what you want to do.  Initially create a volume of a limited size, and leave the rest available to expand into later if you choose.  It can also move logical volumes back and forth between physical volumes on the fly.  When I got an SSD, I picked up my root fs and migrated it over to the fast SSD while the system was running.  Also if you later add another disk to the array, you can expand it on the fly using lvm.

As for the disks in a raid5, you don't want to mix different kinds of disks because the array is limited by the size and speed of the smallest/slowest drive.

---

### Post by yota on 2010-10-05
> **BrutalSpoon said:**
> So does that mean that if I wanted to use the 2TB drives and the 500GB drives I'd have to split each 2TB drives into four 500GB partitions? I guess that completely negates the point of the RAID because if one drive were to fail I'd lose the whole RAID, right?

Right, using more than one partition of the same disk on an array is not a good idea... (even if technically possible I suppose!)

I was not meaning to split the larger drive on as many partitions as possible; I was just saying that if you want to use a larger drive in an array that includes a smaller one you have to partition the first to match the size of the second.
Software RAID enables you to mix different sized drives and you can still use the spared space on the larger drive for anything you like, but, as psusi said, the array is limited by the smallest/slower drive.

To further clarify this would be the layout mixing a 1TB and a 750GB drive on an mirror array:

sda 1TB
sda1 750GB Linux RAID autodetect partition
sda2 250GB Linux partition

sdb 750GB
sdb1 750GB Linux RAID autodetect partition

sda1+sdb1=md0 (raid 1 for instance)
sdb2 formatted in ext4 would be a good /tmp /var/tmp /var/spool partition

This is just an example, but I usually find myself using something like this on small servers made from trash-recovered pieces.

---

