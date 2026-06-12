---
title: "Root Processes"
date: 2009-11-03
forum: General Help
---

### Post by carthmen on 2009-11-03
Hello,

  I have found something unusual, at least I don't remember it seeing it happen before, that is before I upgraded to 9.10.

  I have three processes that show up for a few seconds, and the go away, and a few seconds later comeback and repeat.

 I searched the forums and found this thread [http://ubuntuforums.org/showthread.php?t=1191024&highlight=blank+processes](http://ubuntuforums.org/showthread.php?t=1191024&highlight=blank+processes)

Seems the be the same thing, I did the suggested action from that thread however, the command field is also blank. 

  Anyone have any idea what this could be, or another way to find out since the command field is blank.

---

### Post by lavinog on 2009-11-03
```
ps -ef
```
or
```
ps [pid] 
```
where [pid] is the process id number from the system monitor
edit: you might have to enable the id column in the preferences.  You can also enable the command line column

---

### Post by carthmen on 2009-11-03
KK, found it, at least I'm pretty sure it is it.  It comes and goes very fast so it was hard to catch, but it seems that it is screen-lets updating my GPU sensor reading. :p

So it's all good, thanks for the tip.

---

