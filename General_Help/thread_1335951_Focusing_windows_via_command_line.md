---
title: "Focusing windows via command line"
date: 2009-11-24
forum: General Help
---

### Post by Washer on 2009-11-24
is there a terminal command for switching to a certain window/program by name, or a certain workspace? I need to feed it to a script.

thanks

---

### Post by lykwydchykyn on 2009-11-24
Yes -- wmctrl.  You'll need to install it, though: 
```

sudo aptitude install wmctrl

```

It can do most window management tasks via command.

---

### Post by Agent ME on 2009-11-24
Try out _[xdotool](apt:xdotool)_. Use this command to find the id of a window:
```
xdotool search "Firefox"
```
and this command to switch to a certain window id:
```
xdotool windowactivate 12345
```

---

### Post by Washer on 2009-11-24
Awesome. Thanks.

---

### Post by kaibob on 2009-11-24
> **Agent ME said:**
> Try out _[xdotool](apt:xdotool)_. Use this command to find the id of a window:
Thanks Agent ME. I use wmctrl a lot, and xdotool does things that wmctrl won't do or does only with work. Nice find.

---

