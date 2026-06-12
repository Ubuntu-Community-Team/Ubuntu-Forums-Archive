---
title: "can't find and clean the Trash in ubuntu"
date: 2009-09-29
forum: General Help
---

### Post by attilab on 2009-09-29
now this question will get more complicated
my son's M50SV laptop w/ dualboot (Vista/Ubuntu 9.x)
the boy downloaded a bunch of torrents (rar archives), unpack and delete (what is called a trial and error learning curve) ending up with 0 (zero) space.
1.)I've meant to start cleaning it up, the Trash icon is there on the task bar, but is full of many things, want to empty, click it, but after opening it next time still all there and full. I can't empty it.
2.)I have opened the File Browser, there is the icon again, won't empty it there neither
3.) ALT+F2, type
gksu chown $LOGNAME ~?.local/ share/Trash -R
blinks for a portion of the second and nothing happens further
4.) Ctrl+H to unhide the system, the Trash is not listed there

any idea pls?

---

### Post by drs305 on 2009-09-29
attilab,

I wrote a few guides a while back that may help you. The first is about finding and emptying Trash, which eventually led to the second, which is about finding and recovering disk space.

[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Trash that belongs to root can't be deleted by a normal user without using administrative rights. Also, if you are deleting things from the Trash bin, use SHIFT-DEL. Using DEL only moves it to .... the Trash!


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by attilab on 2009-09-29
thanks for this, but just a minute before your reply I have managed somehow !! (have noidea still) with the command 
sudo rm -r ~/.local/share/Trash/*
I was under impression that was for ubuntu 8.x and we are @ 9.x
also, I can not see the .local/share/Trash/  its not there...
thanks for your reply, I will definitely go now and read it

---

