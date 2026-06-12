---
title: "Trouble Getting Mouse Cursor To Work With Two Separate Monitors On X11VNC"
date: 2011-07-22
forum: General Help
---

### Post by hayhursm on 2011-07-22
Hello everyone,

I have two separate monitors: display :0.0 & display :0.1 and I only need to access display :0.1 which I can successfully do.  I am accessing this display through the iPhone app HippoRemote (which just controls the mouse cursor).  However, if I accidentally leave the mouse parked on display :0.0 I cannot move it over to display :0.1  The mouse will move but not over to the correct display.  Is there a way I can get the mouse to sweep over both displays?  I'm also open for other options as well.  Thanks for the help in advance!

---

### Post by krunge on 2011-11-19
The workaround for the 2nd screen :0.1 and the mouse might be solved by adding this option to x11vnc:
```

-xwarppointer

```

More info: [http://ubuntuforums.org/showthread.php?t=1858316](http://ubuntuforums.org/showthread.php?t=1858316)

---

