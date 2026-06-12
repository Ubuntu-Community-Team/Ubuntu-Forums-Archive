---
title: "Nicotine+ opens every time I try to install something"
date: 2010-03-24
forum: General Help
---

### Post by Robot007 on 2010-03-24
I have no idea why this keeps happening, but every time I try to install a program, Nicotine+ opens. First it happened when I installed Comix, and now when I'm trying to install KTorrent it's happening. I keep getting this error:
(nicotine:3390): libglade-WARNING **: Unexpected element <property> inside <widget>.
AttributeError: 'module' object has no attribute 'Element'
In file "(probably) stdin", at (or in the definition that ends at) line 2:
[...]n get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)

Anybody know what to do to fix this?
I'm on 9.10 Karmic.
edit: It happens when I try to uninstall things too.
edit edit: I guess it's marked as a Nicotine+ bug, but they haven't released an update yet.

---

### Post by cogier on 2010-03-24
Start up Synaptic. See if you get any errors and fix if necessary. If not search for "libglade2.0-cil" and set it to reinstall.

Not sure this will help but it should not do any harm.

---

### Post by Robot007 on 2010-03-24
I just was able to remove it so the problem for that is gone. I'll have to try that when I fix my other issues.

---

### Post by StepBack on 2010-04-14
I had the same problem.
I reinstalled libglade2.0.cll or whatever through Synaptic and it didn't fix it. =/

What did you do 007?

---

### Post by tom957 on 2010-06-13
I'm having this problem too. I've tried reinstalling libglade2.0-cil with no avail. Does anyone have new info on this?

---

