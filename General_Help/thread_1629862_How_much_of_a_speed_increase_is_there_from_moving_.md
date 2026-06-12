---
title: "How much of a speed increase is there from moving temp files to RAM?"
date: 2010-11-24
forum: General Help
---

### Post by nolag on 2010-11-24
Many articles on the net say to do this if you have enough RAM.  Some claim that it will even decrease power usage by lowing the writeback to the disk (since it will not need to write to it as often).  Does anyone do this that can speak to either issue?  I have enough RAM, I don't even use swap since I never use all my RAM (I don't think I even use 3GB of the 4 I have).

---

### Post by HermanAB on 2010-11-24
It will only speed up things that use /tmp, for example a web browser, but little else.

---

### Post by efflandt on 2010-11-24
Using tmpfs for /tmp is often recommended for flash drives (USB or SSD) and is what Startup Disk Creator does for bootable iso on USB.  Flash bits cannot be erased individually, it requires erasing and rewriting blocks.  So using tmpfs can save wear and tear on flash memory.

However, some tasks related to ripping audio or video or creating iso files may require a bunch of /tmp.  If you do not have enough /tmp, it may start using swap.  And if you do not have swap (or enough swap) that may stop what you are doing.

Note that /tmp is emptied on every boot, so there is no need to save that anywhere permanent.

---

### Post by nolag on 2010-11-24
> **efflandt said:**
> Using tmpfs for /tmp is often recommended for flash drives (USB or SSD) and is what Startup Disk Creator does for bootable iso on USB. Flash bits cannot be erased individually, it requires erasing and rewriting blocks. So using tmpfs can save wear and tear on flash memory.
 
However, some tasks related to ripping audio or video or creating iso files may require a bunch of /tmp. If you do not have enough /tmp, it may start using swap. And if you do not have swap (or enough swap) that may stop what you are doing.
 
Note that /tmp is emptied on every boot, so there is no need to save that anywhere permanent.
 
For the audio/video ripping, how much RAM do you think it would take in temp files?  If it can fit there I would assume that it would be MUCH faster to do those tasks that way.  Lets use an extreme example, a high def movie (say blu-ray if I can hold the temp files for that in RAM I am sure I can the others :P).

---

