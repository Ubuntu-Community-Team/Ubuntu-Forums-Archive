---
title: "Partitioner doesn't give me &quot;side by side&quot; option"
date: 2009-10-29
forum: General Help
---

### Post by ckillian on 2009-10-29
Trying to install 9.10.  When I get to the point of deciding on the partitions, there is no option to install "side by side".  Only "use entire disk" and "specify partitions manually".

Am I missing something?  Any ideas?

---

### Post by louieb on 2009-10-29
May be you were browsing your hard disk before starting the install and a partition is mounted.

or less likely you have a non-standard partition table. Open System > Administration > Partition Editor. If it shows a blank disk then there is something out of place in the partition table.

---

### Post by ckillian on 2009-10-29
I'm at a loss.  

If it helps, here's a screenshot of the installation screen and also my partition manager...

---

### Post by sickly on 2009-10-29
It says Vista but is it actually windows 7 ? Cause I didnt have the option to install side by side on my new laptop that came pre installed with windows 7, and the ubuntu installer said that it was vista. even though vista and 7 are pretty much the same thing. But that was the only time i didnt see the option before a install of ubuntu.

---

### Post by ckillian on 2009-10-29
Nope, it's definitely Vista.

Any idea how to get this thing working?

---

### Post by louieb on 2009-10-29
The triangle by sda2 in Gparted means it has detected something strange in the Vista partition.  Right click and select information to see what it says.

The installer sees the same and won't try to shrink it. 

Anyway Boot Vista - let it fix its file system - run defrag and chkdsk. Then try the install again.

---

### Post by ckillian on 2009-10-29
Check disk solved it.

Thank you so much.

---

