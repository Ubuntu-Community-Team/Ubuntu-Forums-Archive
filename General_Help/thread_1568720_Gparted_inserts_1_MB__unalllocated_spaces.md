---
title: "Gparted inserts 1 MB  unalllocated spaces"
date: 2010-09-05
forum: General Help
---

### Post by thelugnut on 2010-09-05
Using gparted, version 0.5.1 to make 7 partitions on my hard drive. partitions 1, 2,and 3 are normal. Partition 4 is an extended partition. Within this extended partition, I have partitions 5, 6, and 7. 
5 and 6 for my Linux distributions, with 7 being the linux-swap.
Here's my question. I have unallocated spaces between 5 and 6, each 1 MB in size. I have been using Ubuntu since 2007 and I have never seen this before. I am wondering if I inadvertently clicked a box during installation, or is this something new in gparted.

---

### Post by Gitanes on 2010-09-05
Is Gparted the partitioner that comes with the Ubuntu install cd?  If so, I'm experiencing the same thing which I describe here: [http://ubuntuforums.org/showthread.php?t=1568713]("http://ubuntuforums.org/showthread.php?t=1568713")  I've looked at another computer that I've got Ubuntu and Windows installed on and the same thing there: small amounts of unallocated space.  This was installed back in 2009 though.

---

### Post by RJ12 on 2010-09-05
I think it has something to do with the Linux Geometry of Partitions and Disks which might have something to do with the CHS of the drive, which I don't really understand. I think it is safe to allocate these spaces (but I would make sure you have a backup of everything). It might also be so the partitions are guaranteed not to overlap themselves. This might happen because of the Geometry that Linux and Windows uses. Again I don't know much of this stuff, but can you imagine if Windows and Linux thought that where your HDD partitions were, was different. A beginning of a partition might be in the end of a partition causing an overlap. That is the only thing I can think of. I know someone will be able to give you an explanation, but I know I have these gaps and I don't mess with them, but my computer is fine still. Its is only 1 MB (which to me I can give up, but I understand some people like to have the 1 MB extra.)

---

### Post by thelugnut on 2010-09-06
Okay, so it seems I didn't do it. That's good. Thanks for the replies. Oh I don't mind losing the 1 MB here and there. I just wanted to learn something.:p I definitely plan on leaving them alone.):P

---

### Post by srs5694 on 2010-09-06
This is caused by a couple of converging factors:


[list]
[*]Disk partitioning is changing from aligning partitions to the start of cylinders (which was meaningful and useful a couple of decades ago but is arbitrary and useless today) to aligning partitions on 1MB boundaries (which improves performance on some modern hard disks and RAID arrays; see [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) for details).
[*]Logical partitions require one sector prior to each defined partition for a necessary data structure.
[/list]


If a partition ends at just before a 1MB boundary, then the need for that extra logical partition sector means that there will be 1MB - 512 bytes of unallocated space between the two partitions. There can be other amounts if you're editing an existing partition table, since the alignment might be different for different partitioning tools.

The simplest way to deal with this issue is to ignore it; however, if the gaps offend you or if you just don't like the clutter in the partition list, you can do something else, such as:


[list]
[*]Use a different partitioning tool -- They vary in how they lay out partitions, as well as in how they display the data. Some will ignore these small gaps, thus uncluttering the display. Note that newer or older versions of the same tool can vary, too.
[*]Change alignment options in your partitioning tool -- Newer versions of GParted have options to align partitions to the cylinder, to 1MB marks, or not at all, IIRC. You can play with these options to get the results you want.
[*]Use primary partitions -- Primary partitions don't need the extra sector and so can be aligned end-to-end with no gaps; however, MBR only supports four primary partitions, so this isn't an option for all disks.
[*]Switch to GPT -- The GUID Partition Table (GPT) format supports up to 128 partitions by default (the value can be increased) and doesn't require space between partitions, so you can pack them in with no space between partitions. Windows can't boot from GPT, though, and some GPT partitioning tools (such as Apple's Disk Utility) enforce a gap of 128MB between most partitions.
[/list]

---

