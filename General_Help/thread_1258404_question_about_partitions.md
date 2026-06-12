---
title: "question about partitions"
date: 2009-09-05
forum: General Help
---

### Post by Kristofer Van Orton on 2009-09-05
Okay well I made a link to my downloads folder which is located in my data partition
upon reboot the link no longer works
and upon thinking about it i realized this
i may be wrong though
but since the data drive only mounts when i click on it
is that the reason its not working?
if thats the case
 how can i make the disk mount upon startup
thanks in advance
-KVO

---

### Post by dandnsmith on 2009-09-05
> **Kristofer Van Orton said:**
> since the data drive only mounts when i click on it is that the reason its not working?
Seems quite probable, but not guaranteed.

> if thats the case
 how can i make the disk mount upon startup?
Try System Preferences or System Admin - somewhere there is provision for 
mounting things.

Have you tried the link after causing the disk to be mounted (should work, but there might be another possible cause to be investigated if it doesn't)

Is the drive always present?

---

### Post by astrakhan on 2009-09-05
Hi, you can add a line to /etc/fstab to mount partitions at start up
this is how I make an extra partition mountable at start:

/dev/sda3       /home/barclay   ext2    nodev,nosuid    0       2

you'll have to change it to suit your particulars though :D

---

