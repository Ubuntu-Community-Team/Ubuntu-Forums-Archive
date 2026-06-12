---
title: "Rhythmbox errors out after Mac4Lin installation"
date: 2009-12-13
forum: General Help
---

### Post by RonB123123 on 2009-12-13
Hi, I recently installed Mac4Lin and every time I open up rhythmbox, it refuses to start up. I opened it in the command line to see what was wrong and it outputted:

> 
$ rhythmbox

** (rhythmbox:2668): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:2668): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:2668): Rhythmbox-WARNING **: Could not open device /dev/radio0
TypeError: Cannot create a consistent method resolution
order (MRO) for bases ImplementorIface, Orientable, Buildable
**
ERROR:/build/buildd/pygobject-2.18.0/gobject/pygobject.c:924:pygobject_new_full: assertion failed: (tp != NULL)
Aborted


It worked fine before, after the Mac4Lin install, it wouldn't start using the icon but worked in the command line. Now it doesn't work in either which forces me to use VLC player (I dislike Banshee).

I have also updated my python-gtk2 install to the latest version in the repository. Is there anything I can do to fix this other than uninstall Mac4Lin?

Thanks,
Ron

---

### Post by RonB123123 on 2009-12-13
Help? Is there a python package I need or what can I do to launch rhythmbox?

---

### Post by infra_red_dude on 2009-12-13
Definitely not a Mac4Lin issue as the same does not modify any system files. 

Looks like some update screwed things up. Is this a known bug? See here:

[http://ubuntuforums.org/showthread.php?t=789251](http://ubuntuforums.org/showthread.php?t=789251)
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/448831](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/448831)

---

### Post by RonB123123 on 2009-12-16
It was the Mac4Lin installation. I uninstalled it, and VLC and Rhythmbox now work fine on my computer.

---

### Post by infra_red_dude on 2009-12-17
Can you try only installing the Mac4Lin GTK theme and testing if Rhythmbox crashes now too?

---

