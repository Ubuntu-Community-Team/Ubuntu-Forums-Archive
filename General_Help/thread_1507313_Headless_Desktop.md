---
title: "Headless Desktop"
date: 2010-06-11
forum: General Help
---

### Post by bakegoodz on 2010-06-11
I have been running a Headless computer I VNC into. I upgraded from 9.10 to 10.04 and now it won't start the GUI without a monitor plugged in. I have been unsuccessful in finding a fix. Any ideas?

---

### Post by KeyserSoze93 on 2010-06-11
You could try this:

[http://en.wikipedia.org/wiki/Xvfb](http://en.wikipedia.org/wiki/Xvfb)

Not sure if it'll help...

---

### Post by HermanAB on 2010-06-11
'sudo startx' doesn't work?

---

### Post by bakegoodz on 2010-06-11
No, I can shell in and try to start X and it won't do it without a monitor. Bottom line X will run when a monitor is connected, doesn't when one isn't. I have tested this several times, if a monitor is hooked up when X starts it will run, if unplug it right before it starts-up it doesn't run.

---

### Post by mr clark25 on 2010-06-11
would something like this help?

[http://www.geeks3d.com/20091230/vga-hack-how-to-make-a-vga-dummy-plug](http://www.geeks3d.com/20091230/vga-hack-how-to-make-a-vga-dummy-plug)

---

### Post by bakegoodz on 2010-06-12
Build a dummy plug to trick software? A hack like that shouldn't be needed when one is using opensource software that can be viewed and modified. It may not work anyways. I suspect the X is configured to look for EDID, or plug-n-play information from the monitor, and can't fail over to default monitor settings if it doesn't find it. I need to find a way to modify this behavior. If it can't be reconfigured, I'll have to file a bug report to fix it in X. I'm sure I'm not the only one that uses headless desktops.

---

### Post by bakegoodz on 2010-06-18
Tried a manual xorg.conf, didn't help

---

### Post by tnat on 2010-06-18
I have the same problem without solution.
You can read on here:

[http://ubuntuforums.org/showthread.php?t=1480904](http://ubuntuforums.org/showthread.php?t=1480904)

---

### Post by bakegoodz on 2010-07-16
Couldn't solve this by a config change, but I found a solution that worked for good enough for my particular situation. I ran a long DVI cable to my desktop monitor that was using the VGA connector. That makes X happy.

---

