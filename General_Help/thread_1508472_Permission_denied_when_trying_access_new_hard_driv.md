---
title: "Permission denied when trying access new hard drive"
date: 2010-06-13
forum: General Help
---

### Post by jac0117 on 2010-06-13
I have just got a Samsumg spinpoint hard drive to use with my Ubuntu machine to store my documents.

Everytime I try to copy something to it, I get the following error:
Error opening file '/media/8ec4a1de-a9b1-4ced-bc14-f53b8b4a20c0/Screenshot.png': Permission denied

I formatted the hard drive as reiserfs 

[IMG]http://img156.imageshack.us/img156/8283/screenshotm.png[/IMG]

[IMG]http://img15.imageshack.us/img15/1365/screenshotdevsdagpartedt.png[/IMG]

---

### Post by todak on 2010-06-13
[This]("http://ubuntuforums.org/showthread.php?t=705432") will explain how to give yourself write permission to your new drive. Nevermind that the OP in that thread has ext3 as the file system, it applies to Reiser as well. Most generally, any time that you format the drive to  other than a MS file system, only root has permission to write to the disk.

---

### Post by xennyeh on 2010-06-13
What the user said above. I had the same problem with my Archos 605 player that I use as a hard drive. I switched to root and it worked fine.

---

### Post by techunit on 2010-06-13
There is another way of doing it regarding the fstab but I don't remember the exact things you need to do.

---

### Post by garvinrick4 on 2010-06-13
Put in Live Cd and then open gparted and put your dev/sda1 in gparted window and right
click on it and give it a label. Anything you want and then its mount point will be
/media/(whatever you name it) from then on. You can then use the previous posts
link. On #2 where it says This.

---

### Post by rukiaEnix on 2010-06-13
add your hardrive to /etc/fstab :

```

/dev/sda2      /media/disk  ntfs-3g defaults 0 0

```

instead of sda2 put your drive and instead of /media/disk put your mount point

---

