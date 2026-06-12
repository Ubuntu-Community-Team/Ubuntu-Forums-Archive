---
title: "Title Bar not appearing"
date: 2010-08-02
forum: General Help
---

### Post by devosion on 2010-08-02
This issue has plagued ubuntu 10.04 on all my installations, PC and laptop, and is an infrequent annoyance that needs to be resolved. Basically, after boot up, i'll bring up a gnome window and the title bar will not be there. This means I can't click and drag windows easily, and do other things the title bar lets you do. Is there an easy fix to this that i'm not locating? Also i've tried restarting my X session, by logging out, and the problem persists until I restart the system. And even then the title bar may not load. Very random and frustrating problem.

---

### Post by Raymond2201 on 2010-08-02
Do you have a specific windowing program? Compiz, Emerald, etc?

---

### Post by Quackers on 2010-08-02
This cured it for me

[http://ubuntuforums.org/showthread.php?p=9656977#post9656977](http://ubuntuforums.org/showthread.php?p=9656977#post9656977)

---

### Post by devosion on 2010-08-02
No im just running with the default settings in ubuntu. I've turned on extra visual effects, but thats about it.

---

### Post by WorMzy on 2010-08-02
```
metacity --replace
``` should reload your window decoration.


Check .xsession-errors to see if there's anything in there that may shed some light on why the problem's happening.

Also run 'gconf-editor' and check "/desktop/gnome/applications/window_manager/default" and "/desktop/gnome/session/required_components/windowmanager" and make sure that they're both metacity.

Also, if you use compiz, running ccsm and enabling the Window Decoration plugin may help if you set the Command to "metacity --replace". Enabling the Crash Handler plugin may help if it's compiz that's crashing, just set the other window manager to metacity.

EDIT: You've enabled visual effects, so you are using compiz.

---

### Post by devosion on 2010-08-02
I went ahead and installed ccsm after several failed tweaking attempts where docky stopped working. After I reverted a few settings and installed ccsm I restarted and the title bar loaded. Don't know if it fixed it for good but i'll be sure to keep an eye on that log file if the issue happens again.

---

