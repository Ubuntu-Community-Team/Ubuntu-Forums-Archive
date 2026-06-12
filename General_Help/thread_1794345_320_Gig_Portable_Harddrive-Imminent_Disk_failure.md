---
title: "320 Gig Portable Harddrive-Imminent Disk failure"
date: 2011-06-30
forum: General Help
---

### Post by McTwitch on 2011-06-30
Right, I can't quite remember how I did it, but I've run into a small problem with my 320 gigabyte harddrive. Now, I want to rewrite it to do a dual boot of Kubuntu and Debian. But, when I attempt to format it to ext4, I get an error.

After a few moments, I get a message announcing:Hard Disk Problems Detected, A hard disk is reporting health problems.

Clicking examine, and then SMART Data test, I come to find that most things are either good, or N/A. There are two problem areas, though. Reallocated Sector Count, and Current Pending Sector Count.

I've tried a few times to write over it, but this is new territory for me. Any ideas would be welcome.

---

### Post by Habitual on 2011-06-30
> **McTwitch said:**
> ...I want to rewrite it to do a dual boot of Kubuntu and Debian. But, when I attempt to format it to ext4, I get an error...

This would require different partitions, but you're speaking as if you are only creating 1 ext4 partition.
If your data is saved, then blow away the existing system partition(s) and format as ext4 during the (custom partition layout) part of the installation. ;)

---

### Post by McTwitch on 2011-06-30
Attempting to overwrite it with another OS ends in error, as well. I've attempted zero-ing out the harddrive, but that didn't work (it's quite possible I did it wrong, though).

---

### Post by DawieS on 2011-07-01
I also have one of these 320 GB drives, where the manufacturer "reverse engineered" the SMART status, to prevent unnecessary warranty claims. My drive has **minus** **six** bad sectors since new. Basically there are six extra sectors to replace any others that could go bad, and still provide the full 320 GB storage.

There were lots of threads on the subject when these drives first came out. To turn off the warning at each boot, tick the box at SMART Data "Don't warn if the disk is failing". The manufacturer has since rectified his approach with later drives.:grin:

---

