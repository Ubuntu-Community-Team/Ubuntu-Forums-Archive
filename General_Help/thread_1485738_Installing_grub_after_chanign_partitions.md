---
title: "Installing grub after chanign partitions"
date: 2010-05-17
forum: General Help
---

### Post by syd2o2 on 2010-05-17
How can I install grub after changing partitions with a partition live cd (gparted), since the old grub is no longer working. Usual reinstall won't work here, it'll just reinstall with all the wrong pointers to partitions.

---

### Post by clgy15 on 2010-05-17
What you need to do is boot into the Ubuntu partition using Super Grub Disk or another alternative. And then run this simple command
```
update-grub
```
 
And BAM its all done.
Now if your not using Grub 2 then it gets harder. But if your using any version of 10.04 then your set.

---

### Post by syd2o2 on 2010-05-17
It's 10.04. Thanks.

---

