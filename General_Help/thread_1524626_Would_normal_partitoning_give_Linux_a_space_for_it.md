---
title: "Would normal partitoning give Linux a space for it to be installed?"
date: 2010-07-05
forum: General Help
---

### Post by Abu Azzubair on 2010-07-05
Hello everyone

I've seen a couple of Tutorials on how to make new partitions (on Windows XP) so that you can use that space to do some organizing (as in i.e "a place to save games", another one "for Audio/mp3 files"...etc), and basically the simplest way (that I found up to now) was:

Click on Start menu - right-click My Computer - Manage - Disk Management - Unallocated - right-click Unallocated - New Partition

Then you get a new partition

My question is:

Is that new partition suitable to be Linux Ubuntu's partition? Is that what making a new partition for Linux Ubuntu is, or is it another process?

(It's the first time in my life to to perform the process of Dual-booting, so I'm kinda stuck up to that point Lol)

Very much appreciated in advance O:)

---

### Post by -humanaut- on 2010-07-05
The ubuntu installer will let you select a "side-by-side" installation give Ubuntu like 100GB or however much you want and it will automagically shrink and partition the system for you.

---

### Post by The Cog on 2010-07-05
> **Abu Azzubair said:**
> Is that new partition suitable to be Linux Ubuntu's partition? Is that what making a new partition for Linux Ubuntu is, or is it another process?
From what you posted, the work you are doing in windows is creating a new partition in some un-allocated space. There are two problems with this:

Firstly, any existing computer probably hasn't got any un-allocated space - it's probably already used up by existing partitions. So the first thing you need to do is to **make** some un-allocate space by reducing the size of an existing partition. I think Vista can reduce the size of its own partition while still running.

Secondly, the kind of partition you create with the vista disk manager is **not** suitable for installing linux on. The easiest thing to do is to leave the unallocated space unallocated, and then tell the Ubuntu installer to "use the largest free space". It will then use that un-allocated space and create the partitions it needs - it will actually create two partitions - this is normal. 

Be careful not to choose the option to use the entire disk - bye-bye vista. You should really make a backup first, just in case of mistakes.

---

