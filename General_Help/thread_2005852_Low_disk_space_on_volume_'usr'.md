---
title: "Low disk space on volume 'usr'"
date: 2012-06-18
forum: General Help
---

### Post by oxama on 2012-06-18
from last couple of days, I am facing a problem, every time I login I am getting a message "the volume usr hjas onlu 135.0 MB disk space remaining".

Can you guys help me with its solution

---

### Post by LiamOS on 2012-06-18
This would seem, at least to me, to mean that you have /usr on a separate partition to the rest of your disk, and that it is running out of space.
The easiest way to free up some space would be to remove any large programs that you don't need(If you don't need libreoffice or something else massive), using sudo apt-get remove [program]. Also, I could be wrong, but 135Mb seems a reasonable amount to have free, at least to me. If that number continues to drop, definitely consider doing something.

A better way would be to redesign your partition scheme, if you're comfortable with doing that. What you would do in this case is increase the space allocated to /usr, or have it on the same partition as /. Before doing this, back up all your data, just incase, and make sure you have a good idea of what you're doing. There are an innumerable amount of guides out there for partitioning.

---

### Post by bokopperud on 2012-06-18
Assuming that /usr is on a separate partition and that you're using a FS native to Linux (ext2, ext3 or ext4), you may try using tune2fs with the -m (percentage) or -r (blocks) option.  These FS reserves a certain percentage of your disk for root (so that you always have room for "cleaning up"), and with large partitions, this may be several GB.  This reserved space is not included when df - and perhaps the program giving you a warning - reports free-space.  

By reducing the reserved percentage, df should report more free-space, which will hopefully quell the alert.  As only root will access /usr anyway, you don't really need any space explicitly reserved for root.  

Use dumpe2fs -h /dev/your_partition and look at the "Reserved block count:" line to see how much is reserved.

That said, you're fast running out of space, so perhaps you should concider repartitioning?  At the very least, you should remove some packages you don't use.

PS: I haven't actually tried this - and I don't even know if Ubuntu reserves space for root any longer - but it may help.

---

### Post by oxama on 2012-06-19
This seems to be a contradictory situation. I have ubuntu using wubi on my laptop where this low disk message is popping. On the contrary, I have ubuntu as single OS on my desktop with almost same disk space. and yes ubuntu reserve the space for root user.

---

