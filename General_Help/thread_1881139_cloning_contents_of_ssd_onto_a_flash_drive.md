---
title: "cloning contents of ssd onto a flash drive"
date: 2011-11-15
forum: General Help
---

### Post by wadelockhart on 2011-11-15
Hi,

I am about to install a new 16 GB ssd on my dell mini 9 and would like to clone my existing ssd onto a flash drive. I have found info on how to do that from the terminal using "dd if...", etc. The problem is I do not know the path of the drive that I want to clone. When I go into system> administration> system monitor>file systems, it looks like my existing ssd is partitioned. (Someone told me I may only be seeing a virtual partition). On the "file systems" page there are two lines: on the first line under the "device" column I see "/dev/sda2".   On the second line under the "device" column I see "gvfs-fuse-daemon". (Curious to know why there doesn't appear a path "/dev/sda1")

These are paths, are they not? Is the second one a "virtual" path, and should I use only the "/dev/sda2" path for the cloning? I hope I am making some sense here. 

wl

Dell mini 9, 8.04 Hardy, 4GB ssd, 2GB memory

---

