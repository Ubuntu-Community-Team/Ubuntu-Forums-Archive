---
title: "Delete windows in favor of Ubuntu"
date: 2012-02-10
forum: General Help
---

### Post by Onthebit on 2012-02-10
I have windows xp on one partition and Ubuntu on another partition and I wish to delete windows completely.  Do I have to delete everything and re install Ubuntu?  

It's an older laptop and too slow with both (I am assuming this is the problem)  I am sick of Microsoft and wish to leave them altogether.

---

### Post by nothingspecial on 2012-02-10
This is not the problem. If you dual boot, one operating system on another partition does not effect the one that is running.

---

### Post by Henkdroid on 2012-02-10
Did you use Wubi or did you partition the disk?

---

### Post by Onthebit on 2012-02-10
I partitioned the disk (I think)  :)

---

### Post by Henkdroid on 2012-02-10
Just to be sure, go on disk utility and click on your hard drive. If it is in more than one partition, install (if you haven't got is already) gParted, then make sure to back up anything important, especially from your windows partition, then delete the windows partition using gParted, MAKE SURE YOU HAVE THE RIGHT PARTITION, I can't emphasise that enough. Then click apply and then type in a terminal > sudo update-grub you will now only have Ubuntu installed, you can also stretch the Ubuntu partition to fit the space, but I think you will need to boot into a live CD/USB to do so.

---

