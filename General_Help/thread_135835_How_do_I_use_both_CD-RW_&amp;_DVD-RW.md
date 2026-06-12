---
title: "How do I use both CD-R/W &amp; DVD-R/W?"
date: 2006-02-24
forum: General Help
---

### Post by DaveRowell on 2006-02-24
I have both a DVD-R/W (/media/cdrom0) and CD-R/W (/media/cdrom1).  If I try to open the drive door (push the front button) of the CD-R/W it won't open and something in the system gets all in a huff and refuses to allow access from the DVD-R/W.  Trying to open the DVD drawer by pushing the front button works but trying to access a CD at that point will usually result in a complete system wide lock-up where nothing short of a manual power-down will recover.  I thought that Linux didn't do that??!!

In short the CD-R/W is completely useless.  If I leave it alone the DVD-R/W works like a charm although I haven't fed it a DVD as yet. Here are the drive entries from fstab:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

I notice that there is a link to cdrom0 called /media/cdrom which I know nothing about.

Any way to get the CD working?

---

### Post by Ocxic on 2006-02-24
instead of pushing the button, try right clicking the cd and hit eject. hitting the button doesn't work for everyone all the time. sometime it will work sometimes it won't.

---

### Post by DaveRowell on 2006-02-25
Trying to answer the last post I found such a rats nest that I'm going to file a bug.  There's something screwed up in Gnome or Linux.

Thanks for trying to help.

---

