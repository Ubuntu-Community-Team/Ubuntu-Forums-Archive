---
title: "Ubuntu newbie makes a mess of things :(..."
date: 2009-12-04
forum: General Help
---

### Post by Tidy_Sammy on 2009-12-04
Hello all, I seem to have gotten myself into a pickle! Rather than type out the whole post again, I'm going to link you my problem (on the forum I originally posted it on before being referred here).

Any help would be greatly appreciated, thanks in advance...:)

[Link]("http://futuremark.yougamers.com/forum/showthread.php?t=118394")

[URL="http://futuremark.yougamers.com/forum/showthread.php?t=118394Link[/URL"]
[/URL]

---

### Post by Greenwidth on 2009-12-04
If you can boot Ubuntu with the external drive plugged in, then I would guess you have installed it there. 
It would also explain why the drive has shrunk.

---

### Post by Tidy_Sammy on 2009-12-04
I see, there is around 300GB of space missing though?

How would I go about uninstalling it from the external then? I'm guessing just deleting the folders is a bad way to go around it.

Thanks in advance.

---

### Post by Greenwidth on 2009-12-04
The size would depend on what options you chose during the install.
Is there other data on the drive? I'm guessing you have checked you can still access it ok.

Probably the easiest way is to unplug the external, so there is no confusion as to where it will install, and then re-install Ubuntu.

Before you do, I would recommend resizing your windows partition (to leave space for the Ubuntu install) from windows. I tend to trust windows stuff to windows and Ubuntu stuff to Ubuntu.

You can use the Disk Management util in windows:
start mmc > add/remove snap in > disk management (local) > right click partition for options (if I remember right !)

If you don't have the option of enough space to resize into (and you know there is enough), defrag the drive, windows likes to spread out.

---

### Post by Tidy_Sammy on 2009-12-04
Running a defrag as we speak and then I shall follow the advice you just posted and report back, I really appreciate your help so far...:D

---

### Post by Greenwidth on 2009-12-04
Before you start doing any partitioning I would make sure you have everything backed up!

You can use disk manage to view partitions on the external drive as well. To recover the lost space, you need to either delete the smaller (300Gb?) partition and expand the 681Gb into it, or just format it (to for example NTFS) and have 2 partitions that windows can see - you can assign a drive letter for each. 
Either way you will lose the data in the 300Gb partition, but if you've only just installed Ubuntu there probably won't be anything you want to keep.

Also, can you post a pic of your partitions just to make sure I'm understanding how they are set up.

---

### Post by Leppie on 2009-12-05
If you first install Ubuntu on your internal drive and connect the external drive once Ubuntu has installed completely, you will be able to see what you're about to delete if the partition(s) aren't corrupted.

If you have a live cd, you can change the installation location of grub (i.e. your internal drive).

---

