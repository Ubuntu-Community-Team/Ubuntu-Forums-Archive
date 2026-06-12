---
title: "Problem setting keyboard layout"
date: 2010-11-16
forum: General Help
---

### Post by frankbooth on 2010-11-16
I'll start this thread by clarifying that I'm not using Gnome nor Gnome's keyboard tools since I'm using Lubuntu 10.10 (LXDE).

I've been having some problems setting my keyboard layout...

```
setxkbmap se,"bg(phonetic)"
```

The code above works, but once I reboot the setting is gone and I'm back to my default layout (se).

Is there a way to run the code at every boot (maybe as a script)? Or are there better alternatives? I've searched around on the forums and google and people seem to edit their xorg.conf, it does not exist in newer version of ubuntu however. 

I've heard it's possible to generate a new xorg.conf, but it sounds scary. Will ubuntu use the xorg.conf in addition to the current settings or would the generated xorg.conf override those settings?

If editing xorg.conf is the way to go, what should I add?
I'm using a Asus EEE PC 1001PX if that's going to be any help at all.

Thanks in advance.

---

### Post by frankbooth on 2010-11-17
bump

---

### Post by cavalier911 on 2010-11-18
See this thread:
[http://ubuntuforums.org/showthread.php?t=1608214](http://ubuntuforums.org/showthread.php?t=1608214)

---

### Post by frankbooth on 2010-11-18
Thanks!

Added ```
setxkbmap se,"bg(phonetic)"
```
to /etc/xdg/lxsession/Lubuntu/autostart 

Works great :)

---

