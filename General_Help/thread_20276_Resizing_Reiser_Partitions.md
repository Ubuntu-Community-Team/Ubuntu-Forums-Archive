---
title: "Resizing Reiser Partitions"
date: 2005-03-15
forum: General Help
---

### Post by Kemotaha on 2005-03-15
I have my home directory as a Reiser partition and I want to resize it down.  This means I have to boot form a CD and run something to resize the partitions.

Any Ideas and/or suggestions?

Kemotaha

---

### Post by Xian on 2005-03-15
Resizing Linux partitions can be a very tricky matter. I've know quite a few that didn't go according to plan. However, that functionality is included in the more recent versions of parted. I do know that the Ubuntu installer uses parted so first I would try using that CD from expert mode, attempt to make your partition changes, and then just exit after that process.

If that doesn't work we'll have to find you a LiveCD that does the same.....

---

### Post by Kemotaha on 2005-03-16
I might have found a work around so I don't need to resize it.  I will have to chekc though because it is on my home machine and I am at work.  I have heard horror stories of resizing reiser Partitions so that Is why I asked.  Any one had luck with it?

Kemotaha

---

### Post by WW on 2005-03-16
In my pre-ubuntu distro, I used plain old parted to resize a reiser partition.  I don't know if I did something wrong, or if the problem was a bug in parted, or if the partition already had errors and parted didn't detect them, but the result was a mangled partition that I had to reformat.

Follow the standard advice: Before you attempt to resize your partition, make a backup.

---

