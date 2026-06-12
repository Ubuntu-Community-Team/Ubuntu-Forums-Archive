---
title: "gnome-session-save --logout from a different display?"
date: 2011-06-10
forum: General Help
---

### Post by PGScooter on 2011-06-10
Hi, sometimes (usually when messing around) gnome freezes up on me and I can't even open up a terminal. However, I can switch to a different display via ctrl-alt-1.

How can I logout of gnome session from there? I would like to be able to run a command similar to:

gnome-session-save

Thank you.

---

### Post by bhaverkamp on 2011-06-10
So try it. Looks like it should work. I will have to give this a try myself. Although usually you can just find the problem process and kill it.


bernieh@bernieh-lx:~/downloads/riverbed/bugs/munirVCdropout$ gnome-session-save --help-all
Usage:
  gnome-session-save [OPTION...]

Help Options:
  -h, --help               Show help options
  --help-all               Show all help options
  --help-gtk               Show GTK+ Options

GTK+ Options
  --class=CLASS            Program class as used by the window manager
  --name=NAME              Program name as used by the window manager
  --screen=SCREEN          X screen to use
  --sync                   Make X calls synchronous
  --gtk-module=MODULES     Load additional GTK+ modules
  --g-fatal-warnings       Make all warnings fatal

Application Options:
  --logout                 Log out
  --force-logout           Log out, ignoring any existing inhibitors
  --logout-dialog          Show logout dialog
  --shutdown-dialog        Show shutdown dialog
  --gui                    Use dialog boxes for errors
  --display=DISPLAY        X display to use

---

### Post by linuxinstalledfromhdd on 2011-06-10
> **PGScooter said:**
> Hi, sometimes (usually when messing around) gnome freezes up on me and I can't even open up a terminal. However, I can switch to a different display via ctrl-alt-1.

How can I logout of gnome session from there? I would like to be able to run a command similar to:

gnome-session-save

Thank you.


[http://ubuntuforums.org/showthread.php?t=665536](http://ubuntuforums.org/showthread.php?t=665536)

:popcorn:

---

### Post by PGScooter on 2011-06-10
Thank you for the replies.

I have tried:
```
gnome-session-save --logout --display=:0.0
```

but it says that X11 initialization failed.

I should have mentioned this in my first post. I am using 11.04.

Any other ideas on how I can send this command from a different terminal?

Thank you

---

### Post by PGScooter on 2011-06-11
Any other ideas?

---

### Post by PGScooter on 2011-06-13
bump

---

### Post by bhaverkamp on 2011-06-13
11.04 is not gnome, so I am not surprised. I am not using 11.04 right now; I don't need the grief. I am experimenting with using Xubuntu.

---

### Post by bhaverkamp on 2011-06-13
Did you try a sudo?

---

### Post by PGScooter on 2011-06-15
I tried again with sudo, no luck. Thanks for the suggestion though.

---

### Post by PGScooter on 2011-06-18
Here is the command I was looking for. I was probably not clear enough in my original message.

You can either try the keyboard command alt+print+k
or do ctrl+alt+f1 (if that doesn't work try ctrl+alt+fn+f1)
and then login and execute the following two commands:
sudo service gdm stop
sudo service gdm start

---

