---
title: "Ubuntu eating up HD space?"
date: 2010-10-18
forum: General Help
---

### Post by vorinoch on 2010-10-18
Hey guys, I'm having a bit of an issue with Lucid installed via Wubi.  I stuck the OS on its own partition (30 GB in size), and don't store any large files in the Ubuntu file system (when I download something large I move it to another hard drive.)  I don't have anything wacky or esoteric installed on my system.

I've been consistently having a problem where, after a few hours or a few days of being booted up, Ubuntu warns me that my available HD space is dangerously small.  The amount of available HD space Ubuntu sees then shrinks from a few GB to nothing within a few minutes, and the only way I can seem to solve this is to reboot.  Taking a closer look at what's happening, my Home folder balloons in size until there's no more writable space recognized.  But there are no files being created or added to, so it looks like there's a bug of some sort.  This SEEMS to be correlated with watching videos (or maybe it's the pulling of large files from a mounted directory into RAM? My videos are all on another HD, as mentioned before).  I can generally go a few days without getting the "low space" message, but I can't seem to make it through a full 2-hour movie without getting the error.

Has anyone else dealt with this issue?

---

### Post by matsuzine on 2010-10-18
I'm not sure why this is happening to you, but the first place I would start is doing a disk usage analysis to find out which directory is growing. Back in 8.04, there was a bug that on my hardware caused log files to keep filling up.  In no time, they were eating up GB's of space.  That may not be what is happening to you, but you might be able to narrow it down.

I've used 

du -ch <dir> | grep total 

before to get the size of a directory and subdirectories.  You could probably narrow it down to the particular directory that seems to be ballooning, and see what's growing.

If you leave off the '| grep total' it will just give you a list of subdirs, files and sizes.

---

### Post by vorinoch on 2010-10-18
I will try the command line thing when I get home.  I did use the GUI thing that pops up when the low-disk warning happens, though.  My Home folder's size was reported as absurdly huge (into the TBs, I believe), but arranging the specific files by size shows nothing out of the ordinary.  The total amount of size taken up by the files in Home is less than 1GB if memory serves.  So for some reason it's counting the space as allocated though the files in there don't seem to be affected.

---

### Post by matsuzine on 2010-10-31
Hello,

Did you find a solution to this?  What did you discover?

---

