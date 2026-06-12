---
title: "gddrescue HELP..."
date: 2012-03-04
forum: General Help
---

### Post by jeliot86 on 2012-03-04
I am helping a friend try to recover 3 years of his kids pictures from a Hardrive that has been damaged by shock (dropped it off the counter).  I ran this command

ddrescue -r 3 /dev/sda2 /media/WDUSB/vaio.img ~/rescue.log

after showing about 6 GB of data rescued I accidentally opened the terminal window to full screen and assentially froze the system (or so I thought)  I then hit ctrl-C to stop repair and forced Terminal to open without GUI support.  I used the same command as above assuming this would use the logfile to resume the repair.  But is seems to have started over because it's showing no errsize:
no errors ect.......
BIG QUESTION: IS gddrescue just showing me the current starting point and it did in fact start from the logfile's stopping point or did I do something wrong and am I re-running 2 days worth of repair work.

Side note: right before the assumed freeze the hardrive was make ticking sound as ddresuce tried to repair it, since I restarted the repair it has started making this same sound.  Am I wrong to think that  ddrescue picked up where it left off, which happens to be a bad sector of the hardrive hence the sound it's making

Sooooo Many question....So little answers.....:eek: 
Any help would be greatly appreciated:p

---

### Post by winh8r on 2012-03-04
this might answer some of your questions:

[http://packages.debian.org/sid/gddrescue]("http://packages.debian.org/sid/gddrescue")

hope this helps

---

### Post by jeliot86 on 2012-03-04
> **winh8r said:**
> this might answer some of your questions:

[http://packages.debian.org/sid/gddrescue]("http://packages.debian.org/sid/gddrescue")

hope this helps

Thnx much, I'll get it out and get back

---

