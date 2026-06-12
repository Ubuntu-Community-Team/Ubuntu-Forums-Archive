---
title: "how to reduce reserved space for root on a partition?"
date: 2010-05-19
forum: General Help
---

### Post by jeditech on 2010-05-19
i have a 700GB ext4 partition for storage purposes. By default it has 5% of the space (35GB!) reserved for root, which does not make sense for this partition. how can i reduce this percentage? there is already a lot of data on the partition and i'm afraid that mke2fs would erase all the data. is there a way to change the percentage without touching the data?
thanks for any help.

---

### Post by blazemore on 2010-05-19
Unless you really REALLY have to, don't do this:

```
tune2fs -m 2% /dev/**foo**
```

Don't change it to 0, as this can cause fragmentation.

If you don't know the device location of your external hdd, please post the result of the command
```
sudo fdisk -l
```

---

