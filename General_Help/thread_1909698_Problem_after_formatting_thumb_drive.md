---
title: "Problem after formatting thumb drive"
date: 2012-01-15
forum: General Help
---

### Post by Vimmander on 2012-01-15
So, I have a 2 GB SanDisk Cruzer that I formatted using the "right-click, format" method.  It seems that, although I can select FAT32, there seems to be some kind of parameter that prevents the drive from being recognized under Windows (specifically, Windows 7 Professional, 32-bit).  The drive was a still usable under Ubuntu 11.04.

Naturally, I tried formatting it under Windows, FAT32, default block size, and now the drive works properly under Windows AND Ubuntu.

So, being comfortable with the command line, but inexperienced enough to need to ask for help with mkfs, what arguments do I need to pass into mkfs to make future flash drives R/W capable under Windows and Unix/Linux (hopefully, both in general)?  Maybe something like:


```
mkfs -t vfat path/to/drive
```

But hopefully with more arguments to expand the drive's usability.

---

### Post by bluexrider on 2012-01-15
Unless you wanted to set a partition, that argument would work.

I personally use "Gparted" but that's another story

---

