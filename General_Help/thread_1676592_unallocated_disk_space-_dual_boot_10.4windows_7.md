---
title: "unallocated disk space- dual boot 10.4/windows 7"
date: 2011-01-27
forum: General Help
---

### Post by krcastel on 2011-01-27
I'm fairly new to ubuntu. I set up dual boot with 10.4 (64bit) on a machine with windows 7 installed first. Everything worked just fine but it seems that there is a bunch of unallocated space on my hard drive. Can anyone explain what all the different partitions are and if/how I can "clean it up"? Thanks!

---

### Post by oldfred on 2011-01-27
Welcome to the forums.

One user who tried to "clean up" small unallocated, destroyed his system.

Your sda1 is the windows hidden boot/recovery, sda2 windows system, sda4 Linux / (root) and sda3 a vendor recovery partition.

If you have not, you should use the vendor recovery to create the DVD(s) to restore your system. It is not a windows install, but just an image of your drive as you purchased it. It usually would erase hard drive and restore it to brand new, so backups are still vital. If it lets you create a windows repair CD you should also do that.

You do not have swap. If you have lots of memory that will be ok, but swap is recommended.

The new way of partitioning puts partitions on slightly larger boundaries and leaves a little space between partitions. It used to round down and less than 1MB was not shown, now you see some with slightly more than 1MB and that should not be adjusted. The one 2MB might be changeable. The 100MB at the end of the drive is difficult to get to since it is after the recovery partition. There is no advantage to expanding the recovery. After creating your recovery DVDs you may be able to delete that partition and reuse that space.

---

### Post by srs5694 on 2011-01-27
With the possible exception of the space at the very end of the disk, I wouldn't worry about it.

I can't be positive, but I suspect these gaps are caused by partition alignment issues. This is something that's been changing a lot recently. In the past, partitions were usually aligned to begin on "cylinder" boundaries. Over twenty years ago, this made sense for various technical reasons, but these cylinder boundaries have been pure fiction for at least fifteen years now; partitioning tools have kept at it just out of habit, and to keep a very very old versions of DOS happy. Today, it makes more sense to align partitions on 1 MiB boundaries, in order to improve performance with some types of disks (some RAID arrays, Advanced Format disks, and SSDs). Gaps like you see can result when one partition is created by a tool that uses one alignment method and the following partition is created by a tool that uses another alignment method. Trying to get rid of the gaps is dangerous, since doing so would require resizing the partitions, and that's always dangerous.

Three of your four gaps are under 10 MiB in size, which makes them trivially small by today's standards. Only the gap at the very end is worth paying attention to, at just over 100 MiB, and even that's marginal, IMHO. You might be able to resize that partition pretty safely, since you'd need only change its end point; however, you can't really be sure that your partitioning tool won't try to change the partition's start point to suit its alignment preferences. (Growing a partition's end point without changing the start point is relatively easy, since filesystems' data structures are laid out relative to the start of the partition, so growing a partition just means adding to the existing data structures. Changing the start point means rewriting a large number of existing data structures, maybe even all of them. That can be very dangerous.) Thus, I wouldn't even recommend that you do anything with that partition. If you do, and if you use GParted for the job, look carefully for a check-box or option selector that tells the program how to align partitions, and be sure it's set to *not* align partitions. That will minimize the chance that GParted will change the partition's start point.

---

### Post by srs5694 on 2011-01-27
> **oldfred said:**
> Your sda1 is the windows hidden boot/recovery, sda2 windows system, sda4 Linux / (root) and sda3 a vendor recovery partition.
...
There is no advantage to expanding the recovery. After creating your recovery DVDs you may be able to delete that partition and reuse that space.

Good points. I hadn't paid any attention to what each of those partitions is for when I replied. If /dev/sda3 is deleted, I'd replace it with an extended partition that holds a logical partition; that way, the data structures will be in place to support as many more logical partitions as wanted in the future, although moving and resizing partitions would be required to support partitions of significant size. (The MBR partitioning scheme used on most PCs is limited to four primary partitions, so without an extended partition, you'll never get more than four partitions on an MBR disk.)

---

