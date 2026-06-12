---
title: "Making the Ubuntu Partition Smaller"
date: 2011-09-05
forum: General Help
---

### Post by Teeba on 2011-09-05
Hi there,

I have one SSD with my Windows OS on it, and another 500gb HDD from which I took 130gb as a partition for Ubuntu. 

So the Windows OS is completely separate from my Ubuntu install, which is on the second HDD.

What I would like to do ideally would be to shrink the Ubuntu partition from its current 130gb size to something like 30gb, as I'd like to use as much of the second HDD I have for general storage.

Can anyone here run me through a step by step for how to do this? I've installed Gparted Partition Editor but it won't let me resize the ubuntu partition (greyed out, like all the other partitions).

Also, would resizing the ubuntu partition break the OS like it would with Windows? 

Thanks,

Teeba

---

### Post by dave01945 on 2011-09-05
you can use gparted but you will have to do it from a live cd/usb because you can't resize a partition while it is in use it is also recommended you backup anything important before you do it as if something goes wrong it will break it but most the time there will be no problems

the ubuntu live cd/usb comes with gparted

---

### Post by Teeba on 2011-09-05
Where do I find this live cd/usb thing? And do I want to boot into it to use it? Or can I do it on windows (on a separate hard drive)?

---

### Post by lqlarry on 2011-09-05
Go to USC (Ubuntu Software Center) on your Ubuntu and type in gpart and a program will show up called Gnome Partition Editor.  
 
Upon further review either use an Ubuntu Live CD or USB Thumb Drive and use the gparted with it.  Worst case re-download Ubuntu.  I don't think you can be in the partition you what to edit.

---

