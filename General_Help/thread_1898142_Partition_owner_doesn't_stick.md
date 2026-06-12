---
title: "Partition owner doesn't stick"
date: 2011-12-20
forum: General Help
---

### Post by emil_donca on 2011-12-20
Hi everyone,

I need two of my partitions to be owned by me (not root). To see why I need this read the last paragraph of my post.

The problem is the partition owner gets reset to root everytime I reboot.
I use
```
sudo chown bobo /dev/sda3 /dev/sdb1
```
and then
```
ls -l /dev/sd*
```
to see the outcome.


The reason why I need this is to hand over raw partitions to a windows 7 running inside VirtualBox instance not started as root.

---

