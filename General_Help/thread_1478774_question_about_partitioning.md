---
title: "question about partitioning"
date: 2010-05-10
forum: General Help
---

### Post by erinmbates on 2010-05-10
i have been thinking about making the switch on my laptop from openSUSE to ubuntu.  the only problem is i currently do not have a external hard drive and i have many photos i would like to keep.  Is there a way to keep my /home directory if i switch to ubuntu?

---

### Post by darolu on 2010-05-10
If you have /home on a separate partition, you have nothing to worry about; you can use it in Ubuntu all your files and most of your configurations will remain intact; if you didn't create a separate partition for /home... you may want to borrow an external drive from a friend.

---

### Post by howefield on 2010-05-10
> **erinmbates said:**
> i have been thinking about making the switch on my laptop from openSUSE to ubuntu.  the only problem is i currently do not have a external hard drive and i have many photos i would like to keep.  Is there a way to keep my /home directory if i switch to ubuntu?

Is your /home currently a separate partition ?

Whatever you do, you really should find a way to back up your data, not only because you are going to do something significant with your disk but in any event, what if the hard drive dies ?

If you do not have a back up of your data, it must mean it is not important to you if you lose it.,

There are numerous alternatives to an external disk including online, cd, dvd or flash stick.

---

### Post by Anthon on 2010-05-10
assuming that your laptop has enough free space, you could shrink the current partition, make a new one and move your data there. After that you can reuse the original partition.
After moving the data away you could shrink the suse partition some more and make another (10Gb or so) partition where you install Ubuntu. After that you could dual boot.
Alternatively, mount the suse partition with the data while booted from CD, and move everything in / to a new directory /data. THen during installation select the partitions where to install by hand, and indicate that you do not want to format it. After installation, move the files you want to keep from /data to where you want them, and remove the rest

---

### Post by dino99 on 2010-05-10
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

