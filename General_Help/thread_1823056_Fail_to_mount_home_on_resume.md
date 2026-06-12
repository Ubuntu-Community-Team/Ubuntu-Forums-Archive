---
title: "Fail to mount /home on resume"
date: 2011-08-11
forum: General Help
---

### Post by Onesimus on 2011-08-11
I have an Acer Aspire ZG5 which I have installed Ubuntu on.  There is a 8Gb internal harddisk which has the system files on (i.e. / ), and a SD flash drive of 16Gb that has the /home partition on. 

The /home partition successfully mounts on boot.  However, when the netbook resumes after sleep the /home partition is not mounted.

Closer inspection with Disk Utility, and attempting to mount the disk within Disk Utility gives the following error:

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/mmcblk0p1 is already mounted on /home
mount failed
```

Any ideas would be most appreciated.

---

### Post by Onesimus on 2011-08-12
bump

---

### Post by Onesimus on 2011-08-17
bump

---

### Post by aeiah on 2011-08-17
well, mtab thinks it is still mounted. i suppose you need to investigate what mtab is, and whether you can tell it to refresh or to instruct it to mark the partition as unmounted. it seems the sleep function does try to remount it, but mtab gets in the way.

---

### Post by Onesimus on 2011-08-18
I have no idea what mtab is.  The man pages don't mention it.

I googled it, and that revealed that it lists all mounted devices - but don't quite know how to proceed.

Anyone got any ideas ?

---

### Post by Onesimus on 2011-08-23
bump

---

### Post by Onesimus on 2011-08-28
bump

---

### Post by Toz on 2011-08-28
There are some suggestions here: [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877]("https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877"). Posts #50, #43, #29, and a few about a backported kernel look interesting and may be worth a try.

---

### Post by Onesimus on 2011-08-28
> **Toz said:**
> There are some suggestions here: [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877]("https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877"). Posts #50, #43, #29, and a few about a backported kernel look interesting and may be worth a try.

@Toz
Many thanks for sending this.  I will give it a go.

---

