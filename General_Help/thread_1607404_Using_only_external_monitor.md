---
title: "Using only external monitor"
date: 2010-10-27
forum: General Help
---

### Post by rmcellig on 2010-10-27
I have an external monitor attached to my laptop. I only want to be able to use that screen and not have anything show up on my laptop screen when the monitor is plugged in. Is this possible? Do I have to go into the Nvidia settings somewhere to make the changes if this is possible?

---

### Post by utilitytrack on 2010-10-27
Yes, it's possible. Use **xrandr** for this. Example:
```
$ xrandr --output LVDS1 --off
```

Here LVDS1 it's a name of built-in screen of your laptop.

---

### Post by rmcellig on 2010-10-27
I tried that but this  is what I got:

randy@mom-laptop:~$ xrandr --output LVDS1 --off
xrandr: Failed to get size of gamma for output default
warning: output LVDS1 not found; ignoring
randy@mom-laptop:~$

---

### Post by utilitytrack on 2010-10-27
Read this:
```
$ man xrandr
```

---

