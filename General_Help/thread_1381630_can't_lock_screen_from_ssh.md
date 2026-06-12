---
title: "can't lock screen from ssh"
date: 2010-01-15
forum: General Help
---

### Post by v1nsai on 2010-01-15
I'm trying to use 'gnome-screensaver-command --lock' to lock my computer so that when my girl is on it I can piss her off :)

I can run the command from the terminal and it works just fine, but when I ssh into my computer and try to do it, I get the error 
```
** Message: Failed to connect to the D-BUS daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
```

Can anyone help me get around this?  It'd be nice to be able to lock my screen from wherever.

---

### Post by Brandon Williams on 2010-01-15
The command has to know which display you're trying to work with. This command line will tell it.
```
export DISPLAY=:0.0
```
That's probably all you need to do before running the command to lock the screen.

---

### Post by v1nsai on 2010-01-17
brilliant, works great.  Thanks a bunch!

---

