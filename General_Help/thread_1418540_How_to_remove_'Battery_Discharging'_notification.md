---
title: "How to remove 'Battery Discharging' notification?"
date: 2010-02-28
forum: General Help
---

### Post by wkoerber on 2010-02-28
I'm running Ubuntu 9.10 on my laptop, and every time I unplug my laptop from power it notifies me that my battery is discharging. The window appears in front of anything  I'm doing, but is not the active window, forcing me to mouse over and hit OK every time I unplug my laptop from power. Is there any way to remove this redundant notification altogether.

---

### Post by MetroPietro on 2010-04-19
I just want to bump this post because I have exactly the same issue and it irritates me for exactly the same reason. Furthermore, why can't we access control of this notification popup via the preferences in the battery applet?

...Ah, found solution with next webpage I searched:
gconf-editor > apps > gnome-power-manager > notify...
uncheck the "discharging" notification box.
Thanks to:
[http://ubuntuforums.org/showthread.php?t=1316642](http://ubuntuforums.org/showthread.php?t=1316642)

---

### Post by MetroPietro on 2010-04-19
[when I figure out how to delete this follow-on msg I will do so.]

---

