---
title: "Deleting partitions"
date: 2006-06-24
forum: General Help
---

### Post by bellaterror on 2006-06-24
Okay, I am in fdisk and when I hit    d     it says slected partition 1 arne't you suppose to hit d then enter then the number of the parition you want to delete then enter again?  please tell me if I am mixing this up somehow.](*,)

---

### Post by wyohermit on 2006-06-24
I'm not quite sure where you are at in fdisk, but you might be more comfortable and safer in a partition manager with a GUI.  Such as cfdisk or more probably gparted.  

Ken

---

### Post by aysiu on 2006-06-24
You can't delete a partition if it's mounted.

Also, you may find it easier to use a graphical partitioning tool (which allows you to unmount a partition just by right-clicking it): ```
sudo aptitude update
sudo aptitude install gksu gparted ntfsprogs
gksudo gparted
```

---

### Post by bellaterror on 2006-06-24
Thank you I'll give these a check I am having different problems now though instead of that if you'd help please come here

[http://ubuntuforums.org/showthread.php?p=1177091#post1177091](http://ubuntuforums.org/showthread.php?p=1177091#post1177091)

---

