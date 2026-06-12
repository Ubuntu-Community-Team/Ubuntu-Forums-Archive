---
title: "Graphical glitches with new Flashplayer"
date: 2011-02-19
forum: General Help
---

### Post by kaldor on 2011-02-19
I installed the newest Flash player in an update a few days ago, and now ever since last night, every time I watch a Flash video I get graphics problems. It looks as if the Flash video is stuck in the centre of the screen and if anything black (text, notifications) are in the way, they show the video behind them. Hard to explain what I mean :) Nothing shows up when I run *ps ax*.

In addition, all Flash videos are now jumbled up with pixels and weird looking glitches.


- Happens with Firefox, Minefield, and Chromium.
- Using latest proprietary NVIDIA drivers available in Jockey
- NVIDIA Geforce 8400m graphics
- Restarting or using Ctrl-Alt-Backspace always fixes the problem.

---

### Post by kaldor on 2011-02-19
It seems Google Chrome does not have this issue. I assumed it was a Flash problem, but it appears to be a Firefox issue. Chromium is affected too, but all seems fine when using Chrome Stable.

---

### Post by dino99 on 2011-02-19
is it on 64 bits ? i've no trouble on i386 here. Maybe you can remove/purge then reinstall flashplugin-installer from synaptic

---

### Post by sceadu on 2011-03-29
I had the same problem. This worked for me (disabling hardware acceleration):

[http://ubuntuforums.org/showthread.php?p=10469877](http://ubuntuforums.org/showthread.php?p=10469877)

Note that it seems to be more of a Flash problem than a browser problem. I'm not sure what voodoo Google  does to get it to not glitch (in Chrome.. I didn't run anything in Chromium), but the same exact behavior existed in Firefox and in Opera on my computer.

---

