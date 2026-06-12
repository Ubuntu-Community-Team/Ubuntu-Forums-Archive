---
title: "partition problem!!!"
date: 2011-03-27
forum: General Help
---

### Post by vivek.pandey on 2011-03-27
hi everyone
  when i installed ubuntu  had allocated around 40 gb to file systems and 40 gb to ubuntu(i mean that home directory , documents and other such stuff)remaining windows. but i find file system use only about 4gb of that 40 gb and so i want some 30 gb out of it to merge in ubuntu partition (home directory one where i store things) how can i do that. if i try to remove space from file system i guess that space will become unallocated and then it would be hard to merge to ubuntu partition

---

### Post by Legeril on 2011-03-27
Create a GParted live CD, boot from this and you will be able to resize your partitions. Make sure you back up your stuff and the partitions are unmounted, GParted can't resize anything if the partition is currently being used.

---

