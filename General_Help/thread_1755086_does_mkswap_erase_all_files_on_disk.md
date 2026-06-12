---
title: "does mkswap erase all files on disk?"
date: 2011-05-10
forum: General Help
---

### Post by ZephyrWing on 2011-05-10
Hi guys, I am totally new to linux, and I was wondering about making swap spaces on my hard drive partitions.

When I call mkswap on a certain partition, does it erase everything there? or does it just find all the free space to use as swap?

Thanks in advance.

---

### Post by WorMzy on 2011-05-10
It replaces the filesystem with swap. All your files will be lost (for a given value of "lost" -- you may be able to recover them with data recovery software if you don't actually write to the newly created swap partition)

---

### Post by ZephyrWing on 2011-05-13
Hmm, so you always need an empty partition to make as swap (besides swap file). Could mkswap only use the free regions on the hard disk?

---

### Post by lithopsian on 2011-05-13
mkswap called on a partition will effectively wipe that partition.  You will lose everything on it.  Normally you would create the partition first, explicitly as a Linux swap partition, but mkswap doesn't care if you did this.  It doesn't exactly erase the files but it certainly makes it hard to recover them and will eventually write over them.

mkswap can also be called on a file.  Again, the file should be created explicitly first in a particular way, but if not then mkswap still goes ahead and will damage any regular file that you call it on.

In your case, if you have a partition that is used for other things and wish to create some swap, you have two options.  One is to shrink the partition and use the freed space to create a swap partition.  The second option is to create one or more files to use as swap files.  Swap files cannot (easily) be used for hibernation but in all other respects they work just as well as swap partitions.  You should use the dd command to create a swap file before you call mkswap, otherwise the file may not work properly as swap.

Finally, you will need to put the file or partition into fstab or call swapon in a script somewhere in order to activate the swap each time you boot.

---

