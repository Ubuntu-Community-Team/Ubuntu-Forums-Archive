---
title: "Run metacity automatically"
date: 2010-09-29
forum: General Help
---

### Post by walkingbeard on 2010-09-29
Hi,

I recently broke my desktop environment.  I had installed e16 and although I reverted to the pure GNOME option at login, it continued to use e16's window manager.  When I uninstalled e16, no window manager was present, but after a while, I worked out that I need to run metacity.

At the moment, I only know how to run it from the command line:

```
metacity &
```Is there a way to get it running automatically?

Thanks,

Beard

---

### Post by kerry_s on 2010-09-29
check in gconf-editor-> desktop-> gnome-> session-> required_components

see pic

---

### Post by WorMzy on 2010-09-29
Also worth checking in gconf-editor is /desktop/gnome/applications/window_manager/default, although that key is depreciated, so I don't know whether Ubuntu still uses it or not.

---

### Post by hhh on 2010-09-29
If you start Metacity from the run dialog (Alt+F2), doesn't it persist after reboot?

---

### Post by TwelveGauge on 2010-09-29
you could write a bash script to get it running at start up. Though you should add a sleep of like 20 to it.

---

