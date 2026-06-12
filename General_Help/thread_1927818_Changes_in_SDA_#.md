---
title: "Changes in SDA #"
date: 2012-02-18
forum: General Help
---

### Post by pdlethbridge on 2012-02-18
I have a little problem that may need an expert help. I have the following screen shots that show what is going on. Mint on a boot up shows up as sda7 but in start up manager it shows as sda5. The partitions are as follows, sda1 is U10.04, sda2 is U10.10  next partition is the swap file and the balance is the extended partition, where Mint shows up at Sda7  after 11.04 which is in the sda5 and 11.10 which is in the sda6. Why are there number changing

---

### Post by dcstar on 2012-02-18
> **pdlethbridge said:**
> I have a little problem that may need an expert help. I have the following screen shots that show what is going on. Mint on a boot up shows up as sda7 but in start up manager it shows as sda5. The partitions are as follows, sda1 is U10.04, sda2 is U10.10  next partition is the swap file and the balance is the extended partition, where Mint shows up at Sda7  after 11.04 which is in the sda5 and 11.10 which is in the sda6. **Why are there number changing**

Because **different** OSs treat things **differently**.

---

### Post by btindie on 2012-02-18
What's the output of ```
sudo parted /dev/sda print
```It may be that the ordering of your partitions has got mixed up and the various programs are treating it differently. For instance it mat be the 5th entry in the partition table but in terms of location on the disk it could be 7th. Try running ```
sudo fdisk /dev/sda
``` and it might complain that they're not in the correct order, you can get it to reorder them but it may affect some of your other OS's depending on how they reference them - either via device/LABEL/UUID but that can easily be fixed with a recovery disk, Ubuntu tends to use UUID so that won't be an issue.

---

