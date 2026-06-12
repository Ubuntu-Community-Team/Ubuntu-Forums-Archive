---
title: "Disable gnome-screensaver on startup"
date: 2011-01-18
forum: General Help
---

### Post by Larkas on 2011-01-18
Hello there, guys. I'm using a multi-session installation, the first being Ubuntu and the other Xubuntu. As I installed Ubuntu first, there were a bunch of GNOME apps running in my XFCE environment. It isn't much of a problem to stop most from starting, except for gnome-screensaver, which, along with it, sometimes starts gnome-power-manager. It can't really keep track of my laptop's battery info (something that xfce4-power-manager does perfectly), so it's just an useless process hanging around.

I wanted to keep gnome-screenshot from starting in the Xubuntu session. Is there any way to achieve this short of uninstalling it completely? All things considered, I still wanted gnome-screensaver to keep loading in the Ubuntu session.

Any help on the matter would be greatly appreciated!

---

### Post by sum1nil on 2011-01-18
probably some setting in 'gconf-editor'

I would try /apps/gnome-session/options/splash_image
and blank it out.

Let us know :)

---

### Post by Larkas on 2011-01-19
Unfortunately, that didn't work =/

EDIT: After reading [https://bbs.archlinux.org/viewtopic.php?id=107779](https://bbs.archlinux.org/viewtopic.php?id=107779), I accessed **/etc/xdg/xfce4/xinitrc** and searched for the following fragment:

```
# Launch xscreensaver (if available), but only as non-root user
if test $UID -gt 0 -a -z "$VNCSESSION"; then 
    if test x"`which xscreensaver 2>/dev/null`" != x""; then
        xscreensaver -no-splash &
[B]    elif test x"`which gnome-screensaver 2>/dev/null`" != x""; then
        gnome-screensaver &
[/B]    fi
fi
```

Then I commented the lines in bold. It stopped the gnome-screensaver from appearing at startup!

I noticed, though, another problem... Please read on:

Even though the startup sequence doesn't start gnome-screensaver,  nm-applet DOES. I use a wireless connection, and whenever the dialog  that says that a network was found or that it was unable to connect to a  network, the gnome-screensaver process starts! I have no idea as to  what is the connection between the two, can someone please help me?

---

### Post by Larkas on 2011-01-20
Any thoughts?

---

### Post by Larkas on 2011-01-20
Any thoughts?

---

### Post by Larkas on 2011-01-20
Any thoughts?

---

### Post by Larkas on 2011-01-20
Any thoughts?

---

### Post by Larkas on 2011-01-20
Any thoughts?

---

### Post by Larkas on 2011-01-27
So... I'm guessing I really have to uninstall it?

---

