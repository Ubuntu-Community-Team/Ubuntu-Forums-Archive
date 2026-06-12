---
title: "Why is there no default read/write access to partitions?"
date: 2009-07-14
forum: General Help
---

### Post by sbjaved on 2009-07-14
I've been using Ubuntu since Dapper. Every time I have to manually edit my /etc/fstab or change the ownership of my partitions via command line to gain read/write access to my partitions. I recently installed Jaunty for a relative. I didn't mount his system partitions during installation. After installation, I clicked the partitions under "Places" just to see if things had improved. Nope, still read-only access because the partition ownership belongs to "root". Why must we jump so many hoops to be able to edit our files...everytime???
To my joy, the usually working method of adding 'rw' to the options in fstab failed as well. I had to 'chown' the partitions to allow the guy to edit his documents. 
P.S: I also tried 'pysdm', which didn't help despite being a good effort. The assistant has no option to add 'rw' to fstab.

---

### Post by ManiacDan on 2009-07-14
Hmmm.  That's weird.  Not only do I have local filesystems mounted, but also remote filesystems, truecrypt partitions, and USB file systems, and they all default to r/w.

Though, now that I check, none of them are in my fstab to begin with except the remote mounts.  Maybe you're making it too difficult.

-Dan

---

### Post by sbjaved on 2009-07-14
I went for the natural way by accessing partitions via Places before messing with fstab. Any ordinary user would've been stumped there...but I've been doing this a while (which defeats ubuntu's purpose of usability and ease of use). The partitions were ext3...not ntfs or hfs, and should've been sanely mounted by default.

---

