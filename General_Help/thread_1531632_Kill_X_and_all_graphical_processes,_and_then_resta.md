---
title: "Kill X and all graphical processes, and then restart them later when I want them."
date: 2010-07-15
forum: General Help
---

### Post by Zorgoth on 2010-07-15
I would like a way to completely annihilate my X while a command line process is running in tty1 (to maximize available memory) and then be able to easily restore it, with all daemons and whatnot running, just by typing startx, after my process is done.  Is there an easy way to do this?

---

### Post by dannyboy79 on 2010-07-15
don't know if there is an easy way but here is an app (link at bottom) that'll tell you what apps are running in the Window Manager, if they are consistent (the number id's), you could write a script to kill them all at once as well as the X server. good luck

[http://bbs.archlinux.org/viewtopic.php?id=68612](http://bbs.archlinux.org/viewtopic.php?id=68612)

---

### Post by WorMzy on 2010-07-15
Daemons run independently of X, so don't worry about them. If you're looking for a way of saving and restoring a GDM session, have a look at gnome-session-save.

---

### Post by Zorgoth on 2010-07-15
After completely trashing my system, I have come to the conclusion that messing with X like that is for greater geeks than I, at least for now.  I will content myself with logging out.

---

