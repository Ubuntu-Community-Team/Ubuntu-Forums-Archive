---
title: "Gnome system monitor does not start"
date: 2009-11-05
forum: General Help
---

### Post by Daniel_le_Rouge on 2009-11-05
Hi!

Last week I installed Karmic on a HP Pavilion ze2000 (Intel Celeron M 1.30 GHz, 480 MB RAM). Every thing worked out fine, but there are some minor problems remaining.

The most important is the Gnome system monitor. I cannot start it anymore.

That's my terminal output:

```
daniel@daniel-laptop:~$ gnome-system-monitor
/home/daniel/.themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/daniel/.themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/daniel/.themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/home/daniel/.themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

** (gnome-system-monitor:1960): WARNING **: SELinux was found but is not enabled.


GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted
```

Does somebody know where the problem is found and how I can solve it?

Thanks a lot!

---

### Post by ExiMoR on 2009-11-05
Same here...

> gnome-system-monitor

** (gnome-system-monitor:3142): WARNING **: SELinux was found but is not enabled.


GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted
Karmic is epic fail... I had NO PROBLEMS on 8.10 or 9.04...
I've much more problems with karmic after upgrade..
That's suckz that I've no time now.. When I have, I'll remove ubuntu and install any better more usable linux or osx86.. It's so sad, cuz I was very happy ubuntu user for some years..

edit:
I've found:
[http://ubuntuforums.org/showthread.php?t=1289649](http://ubuntuforums.org/showthread.php?t=1289649)
but removing Global menu panel applet nor changing theme doesn't help..
edit: Disabling and removing global menu helps..

Firefox segmentation fault problem: Remove tray addon (plugin, that allows you to minimalizeff to "tray") -go to /home/username/.mozilla/*.default/extensions, manually search for it and remove whole {*} directory...
Wohoo! :) It taken me some time to figure out why is my ff crashing :)))

---

### Post by waltercool on 2009-11-11
Just remove gnome-globalmenu :popcorn:

---

