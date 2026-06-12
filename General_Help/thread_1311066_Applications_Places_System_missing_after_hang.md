---
title: "Applications Places System missing after hang"
date: 2009-11-02
forum: General Help
---

### Post by jerrylamos on 2009-11-02
New install of 9.10 Karmic RC from daily build 20091028 running O.K. for a couple days then during a Launchpad comment update the desktop froze tight.  Power off time.  

This is a 2.0 gHz Celeron intel i845 graphics IBM ThinkCentre that has been running Karmic alpha's and beta's with usual early release problems now seem to be fixed.

Nothing in "crash" or logs that I could see.

It's now running again except these items now missing from gnome top line:
"Browse and run installed applications" applet, Applications, Places, System 
I don't seem to see them in the Add to Panel choices.

I can get to System Places from Alt-F1 so these functions still work.

I could install all over again, but I would prefer to be able to restore the functions in case there's another hang.

Thanks, Jerry

---

### Post by Andreas1 on 2009-11-02
try the following (in a terminal):

```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```


this restores all settings of the gnome panel to default and kill will make it restart for the change of settings to take effect (with other applications restarting should not be necessary but the panel is a mess)

---

### Post by jerrylamos on 2009-11-02
Andreas1,

Thanks!  I made an executable file from your code which worked beautifully!

Jerry

---

