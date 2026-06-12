---
title: "Repair NITIX ReiserFS"
date: 2006-05-19
forum: General Help
---

### Post by hhannemann on 2006-05-19
Hi, I have a corrupt reiserfs partition out of a Nitix box I need to repair to gain access to the data on it. (Damn drive crashed 2day and will not boot in Nitix. Used the Nitix diag cd to determine that there are errors on the drive.) However, Ubuntu will not allow me to mount and I cannot figure out the command for reiserfsck. It tells me it cannot find the superblock. A. Which of the partitions (there are 5) would it be on; so I can rebuild it? B. How can I mount the partition to check what is on it (cannot do it from the Settings. C: How do I create a mountpoint I can mount it into. System tells me that the mountpoint does not exist when I run mount -t /dev/hdb5 /mnt/reiser5
Thx for the assistance.
Cheers
Hendrik

---

### Post by AnRuaRi on 2006-05-21
I'm having trouble with Corrupt data on a ReiserFS Drive under UBUNTU. It's still mounting but the computer keeps crashing.

I did find an interesting article which might help here, although I've not had any joy, it does detail information about recovering superblocks.

[http://www.linuxjournal.com/article/193]("http://www.linuxjournal.com/article/193")

HOpe this is of some help

---

