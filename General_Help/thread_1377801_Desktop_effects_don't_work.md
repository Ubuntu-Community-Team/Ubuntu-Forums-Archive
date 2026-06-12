---
title: "Desktop effects don't work"
date: 2010-01-10
forum: General Help
---

### Post by llawwehttam on 2010-01-10
Since I installed 9.10 I have been using CCSM for the desktop effects. Today I noticed that they were not working when I try to switch viewpoints with the mouse wheel and that the ctrl+atl+left/right shows a really old workspace switcher. 

I tried to re-enable it in the visual effects settings but it simply says 'cant enable'

By this I mean that visual effects are set to 'No effects' and I can't seem to re-enable them even though they used to work.

It worked up till yesterday.

I am using an old card with opensource drivers but its been fine until now.

Any help appreciated.

---

### Post by warfacegod on 2010-01-10
Check to make sure your (recommended) driver is activated. Mine used to deactivate every once in a great while.

---

### Post by llawwehttam on 2010-01-10
Its all fixed ( at least I hope so)

I used the advice here: [http://oesediez.blogspot.com/2008/10/vanishing-plugin.html](http://oesediez.blogspot.com/2008/10/vanishing-plugin.html)

It seems to be working.

---

### Post by llawwehttam on 2010-01-10
> **warfacegod said:**
> Check to make sure your (recommended) driver is activated. Mine used to deactivate every once in a great while.

How do I do that. I'm not a noob but that's not my area. lol  I am using the mesa driver and had to downgrade the dri and glz because of a but but it worked after that for a while.

The script works at startup but I would still like to know why it stopped working.

EDIT: just to warn you I can't use the FGLRX driver. My card is ancient and it gives problems.

---

### Post by llawwehttam on 2010-01-10
These outputs may or may not be helpful.

```
llawwehttam@Blackblood:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159]
llawwehttam@Blackblood:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
```

---

### Post by llawwehttam on 2010-01-23
Eventually worked out a temporary fix for this. I had a script in the startup entries running
```
compiz --replace
```

however this stopped working after a while

New thread here: [http://ubuntuforums.org/showthread.php?t=1385261](http://ubuntuforums.org/showthread.php?t=1385261)

---

