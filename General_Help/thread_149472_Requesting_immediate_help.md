---
title: "Requesting immediate help"
date: 2006-03-23
forum: General Help
---

### Post by matrisking on 2006-03-23
Hi,

For some reason, my Ubuntu partition suddenly started acting as if the hard drive was full.  Absolutely full to the point where I cannot even log in because it says something about not being able to write a certain file.

However, I have a paper due tomorrow morning on this hard drive and I'm going to be screwed if I can't log in and access the file.  Any suggestions?  I'm trying a live cd right now, but I'm afraid it might not be able to "see" the hard drive partition that the data is on.

Eternal thanks in advance

---

### Post by dermotti on 2006-03-23
I guess what i would do first is see if you are runnign out of space. And if you are running out of space, clear some up.

If you are not running out of space, i would jsut create a new user to use in the meantime, to get your work done, and research the issue later.

---

### Post by aysiu on 2006-03-23
Okay.

Boot up the Ubuntu live CD.

Then go to Applications > Accessories > Terminal

Type ```
sudo fdisk -l
``` make note of where the partition is where your data is. For the sake of this example, we'll assume it's /dev/hda1

Then ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
gksudo nautilus
```

---

