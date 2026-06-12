---
title: "Creating desktop shortcuts on Unity"
date: 2011-05-24
forum: General Help
---

### Post by salmontres on 2011-05-24
Hi guys,

I'm really liking the shortcuts on Unity. (For instance, if you drag a window against the edge, it gives a window that's half the size of the display, and other touches like that.) I wanted to know if I can make my own. For instance, can I make a command that will send my current program to another workspace if I drag the program to an edge while holding 'ctrl'? (Or shift, it doesn't matter, I just don't want to interfere with the current Unity shortcuts.)

---

### Post by sikander3786 on 2011-05-25
You might need to sacrifice your default Unity behavior then i.e, window edge positioning.

Install CCSM if not already done:

```
sudo apt-get install compizconfig-settings-manager
```

Start up CCSM by searching in the Dash. Go to Desktop Wall > Edge Flipping > Enable Edge Flip Move.

Same for Rotate Cube.

---

### Post by mc4man on 2011-05-25
The first thing you mentioned is called 'grid' (I use rotate/cube here instead of wall so I disable grid.
You should keep in mind that some plugins in ccsm, if enabled or disabled will unset all the plugins

There are alt. means to do those couple of enabling/disablings or even though it may look like ccsm has crashed, it hasn't really - you can just stay in it and re-enable.
After some time you'll know what to put back - till then be careful  or make a list for yourself  - if you open ccsm in a terminal it will list them all, some with truncated names, obviously before messing around
 (unity --reset will restore defaults if need be

The other thing you mentioned can also be done as is by r. clicking in a windows title bar - you'll see the options

---

### Post by salmontres on 2011-05-25
Thanks for the responses!

I began playing with ccsm, but as sikander mentioned, it overrides the Unity defaults when I do something like enable the cube. Thanks mc4man, I didn't know about the r. click command.

---

### Post by sikander3786 on 2011-05-25
> **salmontres said:**
> Thanks for the responses!

I began playing with ccsm, but as sikander mentioned, it overrides the Unity defaults when I do something like enable the cube. Thanks mc4man, I didn't know about the r. click command.
If you want to enable desktop cube, this link might help.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

