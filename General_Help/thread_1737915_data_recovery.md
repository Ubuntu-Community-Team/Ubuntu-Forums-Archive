---
title: "data recovery"
date: 2011-04-24
forum: General Help
---

### Post by yawnmoth on 2011-04-24
On Windows I use a software package called BadCopy Pro to recover deleted data off of hard drives.  What's nice about it is that it preserves the filenames and the directories those files were in.

In particular, what I'm trying to recover are pictures.

I've used foremost as follows:

sudo foremost -t jpg,jpeg -i /dev/sdc2 -o /home/username/dir

Only problem: it dumps everything - like 40,000 pictures - into a single directory.  I can't say for sure but my guess is that more than half of the pictures aren't pictures I care about to begin with - they're probably stuff the browser cached locally.  Also, I have to reorganize everything.  It took a fair amount of time to organize it the first time around and I'm not so eager to spend that time doing it again.

Any ideas?

---

### Post by DeMus on 2011-04-24
> **yawnmoth said:**
> On Windows I use a software package called BadCopy Pro to recover deleted data off of hard drives.  What's nice about it is that it preserves the filenames and the directories those files were in.

In particular, what I'm trying to recover are pictures.

I've used foremost as follows:

sudo foremost -t jpg,jpeg -i /dev/sdc2 -o /home/username/dir

Only problem: it dumps everything - like 40,000 pictures - into a single directory.  I can't say for sure but my guess is that more than half of the pictures aren't pictures I care about to begin with - they're probably stuff the browser cached locally.  Also, I have to reorganize everything.  It took a fair amount of time to organize it the first time around and I'm not so eager to spend that time doing it again.

Any ideas?

Install testdisk using Synaptic and start (in a terminal) the program photorec, which is a part of testdisk. Success.

---

### Post by coldraven on 2011-04-24
Were the folders deleted or was the partition deleted?
If the latter then testdisk can restore the partition but read this first!
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

