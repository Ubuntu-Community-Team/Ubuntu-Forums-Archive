---
title: "xterm has stopped working"
date: 2011-02-25
forum: General Help
---

### Post by MickSulley on 2011-02-25
My laptop is running 10.10 64 bit, fresh install a few weeks back and has been running fine.  This morning I started it up and it went to a terminal login rather than the usual gui login screen.  I can log in but cannot get gui to work.  If I type xterm I get 
xterm: DISPLAY is not set
and
xhost: unable to open display ""

I can boot from live CD and it all works fine, so looks like it is not a hardware problem

I have tried several thing I found by searching but nothing has fixed it.

Any ideas?

---

### Post by Smart Viking on 2011-02-25
run
```
startx
```

---

### Post by MickSulley on 2011-02-25
It fails.  I think the relevant line is

Fatal server error:
no screens found

---

### Post by WorMzy on 2011-02-25
Have you recently made any changes to /etc/X11/xorg.conf?

If yes, undo said changes.

If no, rename aforementioned file with:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then restart.

That should, if the file existed, make Ubuntu use it's default display settings (since xorg.conf is now optional).

---

### Post by MickSulley on 2011-02-25
That has got me into gui again, but it is not right.  I do not have the minimise, maximise close buttons on the windows, cannot move any windows, if I move focus from one window to another the old window stays on top.

Do I need to re install something?

---

### Post by WorMzy on 2011-02-25
Those symptoms suggest that your window manager (metacity by default) has crashed. Try relaunching it by right-clicking on your desktop, creating a new launcher with the command "gnome-terminal", double-clicking it, then running "metacity". If that gives you any error messages, post them here.

If it doesn't give any error messages, press Alt+F2, type "gconf-editor", hit run, then browse to /desktop/gnome/session/required_components, and make sure that the "windowmanager" key is set to "metacity".

---

### Post by MickSulley on 2011-02-26
That has fixed it!!!

windowsmanager was set to gnome-wm

Any idea what could have caused the problems?

Many thanks to all who replied, Ubuntu Forums rock!!!

---

