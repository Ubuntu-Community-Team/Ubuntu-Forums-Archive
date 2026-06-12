---
title: "Ubuntu installation without Deleting Windows Recovery Partition"
date: 2011-04-29
forum: General Help
---

### Post by rasfl3 on 2011-04-29
Hi. Can someone please direct me on how to properly install Ubuntu without deleting the Windows Recovery Partition. Thank You.

---

### Post by mikewhatever on 2011-04-29
Ubuntu installations never ever required the deletion of any Windows partitions. When installing Ubuntu, are you able to identify the recovery partition? Simply don't resize or delete it.

---

### Post by rasfl3 on 2011-04-30
It doesn't touch the recovery partition if I am installing it aside Windows but if you're replacing Windows with Ubuntu completely, it wipes out all the other partitions. I used a Live CD and opened up GParted Partion Manager and just formatted my Windows partition and created the Linux swap partition manually. I then specified the partition I wanted to use for Ubuntu and the Linux swap during the installation leaving my Windows Recovery Partition in tact.

---

### Post by idoitprone on 2011-04-30
live cd 

and
 ```
fdisk -l
```

Make sure you dont have 4 primary partitions on a mbr parition table. If you do, then you will have to delete a partition. At least you are able to back up the partition before you delete it. If you dont have 4 primary partition on a mbr partition scheme. Just go to windows defrag and resize the partition to make room for ubuntu

---

