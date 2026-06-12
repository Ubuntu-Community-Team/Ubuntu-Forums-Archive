---
title: "Partitions using space?"
date: 2010-09-19
forum: General Help
---

### Post by theShaggy on 2010-09-19
This is likely not just an Ubuntu problem, but more about the partitions I'm trying to make.

I have a 164 gigabyte drive that I had partitioned into three (10 gig, 9 gig, and about 136 gigs).  I moved everything off of it, formatted, partitioned, Zero-partitioned, done everything, but unless I am doing a Fat32 format, I keep getting told that nearly 7 gigs of my disk are currently used.

Add to this that Gparted tells me that 2.58 gigs are being used, whereas Nautilus tells me that 7 gigs are used up.  I am confused because there is literally *nothing* on the disk.

Help?

---

### Post by srs5694 on 2010-09-19
Don't worry about it. There are numerous low-level features that consume disk space, even when you've stored no files on the disk. Different utilities have different ways of measuring disk space, so they can produce different results. Examples of things that can cause discrepancies include:


[list]
[*][Binary vs. decimal units](http://physics.nist.gov/cuu/Units/binary.html) (MB vs. MiB, etc.); these suffixes are often applied sloppily, which has been causing confusion for at least three decades.
[*]Unallocated space in disk partitioning schemes. This usually amounts to just a megabyte or so here and there, but sometimes it's more. I doubt if it's an issue in your specific case, though.
[*]Low-level filesystem data structures (inodes, etc.), which consume a certain amount of disk space. This effect is usually pretty small, except for the next item....
[*]The journal on journaling filesystems. This is a special case of the preceding issue, but it's a particularly important one, especially on small filesystems. IMHO, journals don't make sense of filesystems smaller than 1 GB or so because they consume too much space.
[*]Reserved space on ext2/3/4 filesystems. By default, 5% of the filesystem is set aside for use by root, as a sort of emergency reserve in case user activities fill the disk.
[/list]


That last one is the only issue that's easily adjusted by you, unless you've got a small disk and want to disable the journal. The theory of it is that root will be able to log in and fix things even if users fill the disk. In practice,  since Ubuntu disallows direct root logins, this may not work so well.  It's also usually overkill on big disks. You can change the reserved  percentage using the tune2fs utility:

```

sudo tune2fs -m 1 /dev/sda2

```

This sets the reserved blocks value to 1% on /dev/sda2. Change the value and the disk device for your system. Note that this works only on ext2/3/4 filesystems; AFAIK, no other Linux filesystem reserves space in this way.

---

### Post by theShaggy on 2010-09-19
Thank you!  I set it to the minimum and now it seems to be working much better.  Still missing about 10 gigs from the 164 it's supposed to be, but that's not that bad.

---

### Post by shahan on 2010-09-19
you can check the following link. They are specialized on HDD.
[vsrcbd]("http://www.vsrcbd.com")

---

