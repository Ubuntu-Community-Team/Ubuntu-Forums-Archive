---
title: "Slowdowns on fresh install"
date: 2010-10-18
forum: General Help
---

### Post by SmackMyBishop on 2010-10-18
Hey guys,

I just installed 10.10, and fairly often my system slows to a near-unusable crawl.

As an example, playing a non-HD avi from a tmpfs in mplayer will show a frame every two seconds and "* Your system is too SLOW to play this! *".  System monitor shows 0% CPU, 10 gigs of RAM free, and nothing in dmesg.  After a while everything'll go back to normal.

How can I go about diagnosing this?

---

### Post by SmackMyBishop on 2010-10-20
Another issue is that I can't change my background, it seems to be stuck as the GDM background, and I can't see icons on the desktop.

---

### Post by anarchy404 on 2010-10-21
open up the system monitor and see what spikes. try disabling any visual effects if you have them on. and reply because im curious as to what it is!

---

### Post by SmackMyBishop on 2010-10-21
Thanks.

System monitor's process list shows nothing above 1-2% CPU.  (It's a quad-core i7, by the way.)  There looks like a bunch of activity when I go to the CPU usage graph tab, but I can't see much correlation between that and the process list.

My current suspect is the nvidia driver, but still not sure how to confirm...

---

### Post by anarchy404 on 2010-10-21
have you tried going into low graphics mode? have you tried rolling back the driver or installing a new one?

---

### Post by soldier1st on 2010-10-22
are you running 64bit or 32bit?

---

