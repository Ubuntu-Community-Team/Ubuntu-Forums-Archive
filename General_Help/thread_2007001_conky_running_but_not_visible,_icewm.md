---
title: "conky running but not visible, icewm"
date: 2012-06-19
forum: General Help
---

### Post by InkyDinky on 2012-06-19
Conky shows up as a running process under ps, but it is not visible.
It will often start as visible but as I run other programs throughout the day it disappears.
My conky script grabs a background image, parses an rss feed and gets my gmail and gcalendar.
I'm running icewm as the computer is a 1400MHz Intel with 512mb of ram.
I'm guessing the constrained resources have something to do with it all.

Is there any way to get conky to redisplay w/o a restart?
The problem also has the annoying habit of preventing the icewm context menu from showing up when right clicking where the conky display typically resides on the desktop.

Thanks for any help/insight.

---

### Post by HiImTye on 2012-06-19
its likely that it's crashing for some reason if it disappears, check with a ps
```
ps -e | grep conky
```

conky will stop you from being able to use the context menu on it, as conky creates its own window on top of the desktop, just as any other window would prevent you from getting a context menu on the desktop

---

### Post by InkyDinky on 2012-06-22
I know that conky is running as stated in the OP by using ps. However it is not visible on the desktop. It just shows the background image with no overlay of conky.  
Although conky draws its own window, the right-click context menu still works fine when conky is running properly. I just checked as conky is currently running without the strange behavior and I can right click all over the conky window and the context menu pops up.

Any other thoughts?

---

### Post by VCoolio on 2012-06-22
post your conky config so some guru can check. It may be related to the own_window_type setting in there. Did you try something else there, like 
own_window_type panel
or
own_window_type override
There is also "normal" and "desktop", but what desktop is good for, I don't know, it only gives problems.

---

