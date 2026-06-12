---
title: "system crashed?"
date: 2010-08-06
forum: General Help
---

### Post by tamedcynic on 2010-08-06
I did a system update earlier in the day, but I have a hard time thinking this is connected to it:

I shut down my computer and when I went to start it up, I got a black screen and a bunch of letters and numbers followed by 

Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.


Does anyone know what's going on?

Is there something I can do to get back to my desktop?  Is there a way I can access my documents, at least?

---

### Post by flanagan on 2010-08-07
There are a bunch of threads dealing with repairing such a disk error. This one looks good:

[http://wwww.ubuntuforums.org/showthread.php?t=1167710]("http://wwww.ubuntuforums.org/showthread.php?t=1167710")

Found by a Google search for: *ubuntu system startup fail "try passing" bootarg*

---

### Post by tamedcynic on 2010-08-07
I'm not sure what I did that fixed it.  I inserted the Live CD and backed up my files.  When I restarted my computer, I got the Ubuntu splash screen again and it asked to do a system test. After fixing the errors, it has been working well.

---

