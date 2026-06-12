---
title: "Creating partition for home directory"
date: 2011-12-01
forum: General Help
---

### Post by rmcellig on 2011-12-01
I have heard that creating a partition for my home directory is the best and most flexible way to go so that my home directory is  in a separate partition if anything happens to my system or I want to install a new system without harming my home directory. How do i set this up? Is there a guide or better yet a video I can follow?

---

### Post by searchfgold6789 on 2011-12-01
There is a program called Ubuntu Tweak (google it) that can do that quickly and easily. You just have to make the partition first and make note of the partition name, for example /dev/hda1 or /dev/sdb3. Then open Ubuntu Tweak.

---

### Post by Unitux on 2011-12-01
IMHO You should ALWAYS make 4 partitions as minimum, /home / /boot and /tmp.

---

### Post by rmcellig on 2011-12-01
I don't think there is a version of Ubuntu Tweak that works with 11.10 yet

---

### Post by oldfred on 2011-12-01
I do not believe in separate /boot or /tmp for most desktops.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

If you already have an install, you can create a new partition and move your home to the new partition.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

