---
title: "Disk Utility, GParted, differences in formatting."
date: 2012-02-23
forum: General Help
---

### Post by Roasted on 2012-02-23
I noticed something when I was playing around with a spare drive I was trying to prepare to add to my software raid array. While I know how to do most of this stuff in terminal, I was trying to see how the GUI tools worked in comparison.

In Disk Utility, if I format a drive and set the partition type to Linux RAID Autodetect (fd), it works fine. If I go into GParted then, I see the drive has 2 megabytes unallocated.

If I format the drive in GParted in the exact same way, then go to Disk Utility to set the partition type to Linux RAID Autodetect (fd), it sits there and sits there, and eventually times out. But if I go back into GParted to check it, there isn't any free space or unallocated space whatsoever. 100% is to the drive.

I'm just questioning, where are the differences coming from? Why is Disk Utility letting a few megabytes unallocated for yet it works when I set the partition type to Linux RAID Autodetect? The reason I get confused is when I first set up RAID, I did it with the alternate installer CD. The original RAID drive, drive SDA, has 100% of its space in use, not a single megabyte unallocated for, and it's fine in the array. Everything I typed above was in reference to SDB I was playing with, which will be added with SDA to the array.

So anyway, that's where I got confused. What's happening here that Disk Utility and GParted have some spacing differences? Clearly something is going on with Disk Utility because when formatting with Disk Utility, setting the partition type to RAID works fine.

---

