---
title: "Can't print, can't mount USB drive, and I need recovery mode to log in"
date: 2010-05-10
forum: General Help
---

### Post by bledsoe on 2010-05-10
A few days ago I began to get messages about my hard drive running out of space, and while I tried to clear out some files to make room I somehow managed to mess something up such that my main login screen appeared with hugely distorted letters and dialog boxes, and it wouldn't let me log in.  While this is still the case, I can now log in by booting to recovery mode, selecting the netroot option, doing an "su myusername", and then executing "startx".

While this is a little inconvenient, it does bring up my standard Ubuntu operating environment and I now have access to all my files, email, internet, etc.  There are still a few miscellaneous things that are messed up, however, and I don't yet know how to fix them. In particular:

a) I can't print. I tried running the printer configuration tool from the System->Administration menu, but there's no "New Printer" icon. Also, while trying to get it working, I managed to generate a "The cups scheduler is not running" error message.
b) I can't mount a USB drive. Every time I plug one in, I get an error message that says "Unable to mount drive, not authorized."
c) Finally, there's the basic problem of still not being able to login without going thru my recovery mode workaround.

I suspect all these problems are related, though I'd be happy to fix them one at a time if that's what it takes.  Any suggestions greatly appreciated.

---

### Post by narendraD on 2010-05-10
The first suggestion i would make is to obviously create some space by either deleting or backing up data from /home or any data partitions you have. Then if you still cant login normally, we will see.

---

### Post by bledsoe on 2010-05-11
Yes, that was in fact the first thing I did.  Hard drive space doesn't seem to be a problem any more, but I'm guessing that my drive got so full that some other file(s) got corrupted somehow.

---

### Post by narendraD on 2010-05-11
If you have done that already, then i am afraid it is not related to HD space. Something somewhere is corrupted. While i cant figure out what and how to fix it, i would suggest a fresh install after you back up all your data.

---

