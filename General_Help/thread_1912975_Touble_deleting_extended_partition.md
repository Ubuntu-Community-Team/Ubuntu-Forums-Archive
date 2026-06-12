---
title: "Touble deleting extended partition"
date: 2012-01-21
forum: General Help
---

### Post by Creddeus on 2012-01-21
Hey. I'm trying to delete my Windows XP partition with gparted but in order to do that it wants me to unmount the extended Linux partitions I have running. Obviously I can't run Ubuntu if the partition isn't mounted so I was wondering if there was a way to delete that partition and resize my current one either before Ubuntu boots up (possibly with a boot disk) or after it's already booted.

I saw a tutorial online where a guy deleted an extended partition using fdisk but deleting that partition is kind of pointless unless I can resize the one that's beginning to get a little full.

Thanks, guys.

---

### Post by Basher101 on 2012-01-21
You will need to partition it using a Live CD. I highly recommend to NOT move your extended parition, it may mess up your linux and files...


regards

---

### Post by grahammechanical on 2012-01-21
It would be better if you showed us a screen shot. I though that the Windows OS installed into a Primary partition and not an Extended one. It is Ubuntu that creates the extended partition.

Regards.

---

### Post by Creddeus on 2012-01-21
I have squeeze but I'm not experienced enough with the terminal to really use it. Would it be possible to make a gparted boot CD or something of the sort?

---

