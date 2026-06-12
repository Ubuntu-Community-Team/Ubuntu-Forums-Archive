---
title: "Stop the disk check at startup"
date: 2009-07-10
forum: General Help
---

### Post by CbrPad on 2009-07-10
The disk check at startup is driving me crazy, I've got some very large files, and a very large amount of files, and even after pressing Escape, I still have to wait for at least 2-3 minutes before it continues on (I'm presuming it's finishing the file it's at).  

I've tried every'tune2fs' parameter I can think of (frequency, days, weeks, months) to extend the interval but it still seems to stick at the 30 reboots no matter what.  

There is nothing wrong with the drive and it's always shut down cleanly, so what I want to know is how can I turn off this stupid check entirely before I fling my machine out the window ?

---

### Post by doas777 on 2009-07-10
open your FStab with:
```
gksu gedit /etc/fstab
```then find the line that configs the drive in question. the line should end it a '1'. change that 1 to 0, and it shouldn't try to scan it unless there is an unclean shutdown or errors are returned at mount.
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by CbrPad on 2009-07-11
I'll give that a try, many thanks!

---

