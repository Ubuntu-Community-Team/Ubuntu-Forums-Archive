---
title: "how to format"
date: 2006-03-11
forum: General Help
---

### Post by jrjerry on 2006-03-11
i have 2 4g raid 1 harddrives that the ubuntu os  is on but i have 3 9g raid 0 hard drives that it isn't using,how do i format the other hard drives so i can use them

---

### Post by HokeyFry on 2006-03-11
download gparted via synaptic and use it to format it to a linux partition. it is much easier to use than parted, which is a command line program. Gparted is a GUI that does the same thing, and is easier to use.

---

### Post by taurus on 2006-03-11
If you know the name of those three harddrives, assuming /dev/sdb1, /dev/sdc1, & /dev/sdd1, then you can do something like

```

sudo mke2fs -f /dev/sdb1
sudo mke2fs -f /dev/sdc1
sudo mke2fs -f /dev/sdd1
sudo mkdir /mnt/first /mnt/second /mnt/third
sudo mount -t ext3 /dev/sdb1 /mnt/first
sudo mount -t ext3 /dev/sdc1 /mnt/second
sudo mount -t ext3 /dev/sdd1 /mnt/third

```
Otherwise, just add those three new drives into /etc/fstab so they would be automatically mounted upon boot.

---

