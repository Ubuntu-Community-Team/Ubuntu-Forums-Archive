---
title: "How can I expand the volume on which ubuntu is installed?"
date: 2011-06-25
forum: General Help
---

### Post by snare91 on 2011-06-25
On my laptop, there is a 160 GB Hard drive, which was earlier in 3 volumes - all around 52GB. One drive was the one on which I had installed Windows, and the other 2 were for data. Out of those 2, I managed around 15 GB free space, on which I installed Ubuntu 11.04. Now, I figured that I like Ubuntu, and I need more space on this volume.. Is there any way of increasing the volume on which Ubuntu is installed without having to format and reinstall ? I'm a n00b to linux/ubuntu, please help me through this !

---

### Post by TeoBigusGeekus on 2011-06-25
Boot up with a live cd/usb and fire up gparted
```
gksu gparted
```
If it's not on the live cd, install it yourself
```
sudo apt-get install gparted
```

---

### Post by snare91 on 2011-06-25
Thank you. 
I have managed to create 15 GB of free space [unallocated] using gparted. However, the option of Move/Resize my ubuntu volume is not available. What can be done about that ?

---

### Post by TeoBigusGeekus on 2011-06-25
You have to unmount the partition first.
Can you post us a screenshot with the partitions from gparted?

---

### Post by snare91 on 2011-06-25
[http://i55.tinypic.com/wmftjb.png](http://i55.tinypic.com/wmftjb.png)

---

### Post by puntigamer on 2011-06-25
You can do it with a LIVE system. The new Ubuntu live systems have GParted installed, and with it you can manage partitions, such like resize or move your own root partiton, without mounting/unmounting it!

---

### Post by TeoBigusGeekus on 2011-06-25
What do you get when you right click sda7?
The partition has a key in front of it, is it mounted?

---

### Post by snare91 on 2011-06-25
only unmount, manage flags and information.

how can i do this without using a live cd ? because, as long as ubuntu is running, i can't unmount this, and ext4 is not recognised in windows, so i wont be able to get it to expand using windows :s

---

### Post by TeoBigusGeekus on 2011-06-25
You can't do this without a live cd.
In order for gparted to do any operations on the partition, the latter has to be unmounted, hence you can't do it from inside your ubuntu installation.

---

### Post by snare91 on 2011-06-25
Thank you!
The last thing that I want to ask - will expanding a volume cause any problems with the operating system?

---

### Post by TeoBigusGeekus on 2011-06-25
No, on the contrary, it will make your system faster.
However, it is wise to make a backup of your crucial files first.
Also, remember this: once gparted has started, DON'T interrupt it for whatever reason. I once lost 300Gb of data because of this...

---

### Post by snare91 on 2011-06-25
I still can't expand the volume even though i have 15 GB of space and all my volumes are unmounted :s what can it be now ?

---

### Post by TeoBigusGeekus on 2011-06-25
Screenshot and right click of sda7 options.

---

