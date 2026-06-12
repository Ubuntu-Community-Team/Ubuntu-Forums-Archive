---
title: "Partitioning"
date: 2011-07-17
forum: General Help
---

### Post by amnite on 2011-07-17
I have a 220G hd with windows installed on it. The hd is already partitioned but i want to split it in half so i dont have to run a wubi anymore... how would i go about that?

---

### Post by TeoBigusGeekus on 2011-07-17
Boot up with a live cd/usb and fire up gparted
```
gksu gparted
```
If it's not on the live medium, install it with
```
sudo apt-get install gparted
```

---

### Post by Mark Phelps on 2011-07-17
> **amnite said:**
> I have a 220G hd with windows installed on it. The hd is already partitioned but i want to split it in half so i dont have to run a wubi anymore... how would i go about that?

It's YOUR PC, but if you're running Win7, I would strongly suggest NOT using GParted to shrink the Win7 OS partition.  We've seen lots of reports of folks ending up with corrupted, unbootable Win7 systems after that.

Instead, use the Win7 Disk Management utility to do the shrinkage.

Also, while you're in Win7, use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you need to repair the Win7 boot.

---

### Post by grahammechanical on 2011-07-17
I have also seen advice to defrag the disk using a Windows defrag utilty. Less likelihood of data being messed up when it is moved, apparently.

Of course you would uninstall ubuntu and wubi first. Then download a live CD image. Boot from it and select to install alongside of Windows. The installer will take care of the partitioning. The Ubuntu web site has detailed instructions with pictures. Look for Download - show me how.

Regards.

---

### Post by Blasphemist on 2011-07-17
I will step out on a ledge and disagree, respectively, with Mark and agree with Graham. The fact the ubuntu install can and will shrink the windows partition, and given that windows does such a miserable job of shrinking it's own partition, I wouldn't worry about doing all the shrinking with windows.

I would defrag, and defrag, and defrag some more. Way past when it says it doesn't need it. If you were to try then to shrink from windows you'll likely find it won't shrink anywhere near as much as it could. Windows seems to have a terrible time with moving files from the end of the partition. Win 7 will do a defrag when you ask it to shrink then refer to the application error log to find what file it can't move. Should you figure out a way to get past that file, and you often can, it will allow a little more shrinkage on the next attempt but limit the shrink because of another file. You'll get much better success with GParted, in my humble opinion.

I'll also refer you to this site as it is a great dual boot install reference. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by wildmanne39 on 2011-07-17
Hi, also here is a guide to converting wubi to a normal install in case you would like to do that instead. 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

