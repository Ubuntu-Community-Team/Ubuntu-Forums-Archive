---
title: "Need Vista to be able to see Linux partition!"
date: 2009-08-04
forum: General Help
---

### Post by draconastar on 2009-08-04
I'm having trouble getting my current installation of Windows Vista to see my Linux partition on a separate hard drive.  Here's the dilemma:

On my old computer, I had a Windows partition and a Linux partition.  When I got a new computer and new hard drives, I wanted to get all of my old files off of my old hard drive.  The files I wanted were between BOTH partitions, so I would need to be able to see ext3 files.  So what I'm doing is plugging in a second hard drive that has two partitions on it that I am trying to be able to see from my main drive, which only has Windows on it.

I've already tried installing and using Ext2 IFS from fs-driver.org, but it didn't work from what I can tell.  After asking me to label the partitions and restarting my computer, it wants me to format the partitions (which are labeled E: and G: ) before I can use them.  This obviously is a problem.

Does anyone know what I should do in this situation?  I realize it's the fact that I'm trying to use a separate hard drive that's the problem, but I really have no other choice.

---

### Post by merlinus on 2009-08-04
This may help:

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by draconastar on 2009-08-05
Awesome!  That worked out perfectly for me.  Thank you very much!  :D

---

