---
title: "Memory size mismatch"
date: 2011-11-02
forum: General Help
---

### Post by Manyette on 2011-11-02
This is the second time this has happened to my system, and I don't have a clue how it has come about.  Would appreciate any insight into how this happens, or even better, how to cure it.

Single user system Ubuntu 10.10.  System is working just fine and exhibits no problems whatsoever.  But when I check my memory usage, the system monitor reports that my /home directory reports over 20 gigs in use, whereas all other checks show only 5.7 gigs in use, and that is the correct number.

System Monitor
	/home		Used		21.1 GiB

gksudo Nautilus
	/root/home	Properties	5.7 GiB

Nautilus
	/home/don	Properties	5.7 GiB

If I add all the memory usage of each of the directories under /home I still come up with that 5.7 gig number of memory used.  I'm puzzled how the system monitor can come up with such a large number, and where it's obtaining the extra 15 gigs or so. Anyone have a clue?  I'm really baffled.

---

### Post by dcstar on 2011-11-03
Disk space is not "**memory**".

---

