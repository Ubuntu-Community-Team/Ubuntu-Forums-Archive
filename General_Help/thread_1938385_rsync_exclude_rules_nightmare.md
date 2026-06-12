---
title: "rsync exclude rules nightmare"
date: 2012-03-09
forum: General Help
---

### Post by u-slayer on 2012-03-09
I'm trying to get rsync to only copy certain subfolders by name.

This works:

+ A/*Good*/
A/*

But if I want to get sub-sub folders:

This doesn't work:
+ A/**Good*/
A/*

---

