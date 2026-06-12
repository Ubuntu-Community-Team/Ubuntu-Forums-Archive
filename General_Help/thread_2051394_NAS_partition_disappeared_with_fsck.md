---
title: "NAS partition disappeared with fsck"
date: 2012-09-01
forum: General Help
---

### Post by Thibaud74 on 2012-09-01
Hi,

After some difficulties accessing to my NAS network in writing mode (1 TO, bought one year ago), I launched a fsck -yvf; now gparted tells me it gots no partition ...
I made a tesdisk /dev/sdb1> Proceed> Intel> Analyze> Quick search> Yes
After several hours the partition was not found. I did a deeper search, same results.
fdisk gives me no information.
I did
```

sudo mke2fs-n / dev / sdb
sudo fsck-y-b 32768 / dev / sdb

```
I did the second line with numbers from results of the first line, without success.

How can I scan my NAS to access to my files ? The harddisk seems have broken cylender however datas are not erased I suppose. What are tools to access to data on a ext3 broken partition ?

Thanks you,
Thibaud.

---

