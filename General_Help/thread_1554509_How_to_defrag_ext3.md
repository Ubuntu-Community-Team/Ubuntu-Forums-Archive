---
title: "How to defrag ext3?"
date: 2010-08-16
forum: General Help
---

### Post by Capone on 2010-08-16
How is it possible to force defragmentation in a file system?

---

### Post by bodhi.zazen on 2010-08-16
What makes you think you have a problem with fragmentation ?

All file systems fragment, it is unusual that you would have enough fragmentation to affect performance. It can happen if your hard drive is full.

---

### Post by t0p on 2010-08-16
There are a few defrag utilities for ext3 - some program names are bandied about [here]("http://en.wikipedia.org/wiki/Ext3#Defragmentation").  But, as the same Wikipedia page points out, the Linux System Administrator Guide states:

> 
Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.


So, unless you are suffering from problems that you're sure are caused by fragmentation, I'd say you don't really need to defrag an ext3 file system.  I have never defragged an ext3 partition and I don't think it's done me any harm. (But how do I know it hasn't done any harm? If I've never defragged I wouldn't know if it would be worthwhile.  Probably be a good idea to get advice from an expert rather than some anonymous bod on a web forum. ;) )

---

### Post by Capone on 2010-08-16
what does this mean then?

/dev/vg0/lv_home has gone 264 days without being checked, check forced.
/dev/vg0/lv_home: 95704/2097152 files (36.0% non-contiguous), 3452314/4194304 blocks

---

### Post by Ugluk on 2010-08-16
There is an universal defragmentation method: add all files to tar archive on other partition, remove all files and extract them back.

---

### Post by jongkind on 2010-08-17
> **Capone said:**
> How is it possible to force defragmentation in a file system?

Pyfragtools is a winner, read this thread:
[http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551")

---

