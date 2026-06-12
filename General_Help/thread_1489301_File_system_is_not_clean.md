---
title: "File system is not clean"
date: 2010-05-21
forum: General Help
---

### Post by CrazySat on 2010-05-21
Hi all,

I just installed for my first time Ubuntu 10.04 LTS

I can't unfortunatly mount one NTFS partitions (extended partition) of my secondary hard disk, I always get error message and if I try a check with Disk Utility I get "file system is not clear". It is not even listed among available disks in Computer.

I tryed to repair the partition running chkdsk (with all options enabled) with Win XP and some errors were found but after fixing them I always get same message with Ubuntu and I can't access to that partition.

How can I please solve the problem?

Thank you.

---

### Post by James78 on 2010-05-21
Some tools that may be of use to you are.
ntfsfix
ntfsundelete
chkdsk /f (try it again on Windows?)

Here are some links that may be of some use to you.
[http://ubuntuforums.org/showthread.php?t=533958](http://ubuntuforums.org/showthread.php?t=533958)
[http://ubuntuforums.org/showthread.php?t=1431331](http://ubuntuforums.org/showthread.php?t=1431331)

Good luck, and before following some of the more advanced suggestions that may be in the links (which may have a potential to destroy lots of data), wait for others replies, they may come up with something better than I.

---

### Post by CrazySat on 2010-05-21
Thank you for your reply James78.

I already tryed 3 repairs with chkdsk and all its options with Win XP and no longer errors are found.

I will have a look now to links you posted me.

---

### Post by CrazySat on 2010-05-21
The very odd thing is that it was perfectly working with Ubuntu 8.04 LTS I had used up to few days ago.

---

### Post by James78 on 2010-05-21
That's odd. What is the exact error message you are getting? Do you think that it's possible there could be an entry in fstab preventing you from mounting?

---

