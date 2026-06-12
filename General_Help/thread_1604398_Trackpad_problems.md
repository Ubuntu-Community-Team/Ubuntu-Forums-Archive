---
title: "Trackpad problems"
date: 2010-10-24
forum: General Help
---

### Post by fo rizzle on 2010-10-24
I'm having issues with the track pad on my HP dv6000 running 10.10 with kernel 2.6.32-25-generic (though it happens in another kernel I switched to for testing). I can boot normally (I have tried a few kernels) to the login screen. There I choose my session (GNOME and GNOME recovery both have the problem). At this point, the trackpad is still working. The cursor is sharply angled. Then, the screen goes blank as GNOME starts (track pad still working). Then the cursor changes to a "plump" cursor, then switches back to the angled one. At this point, the trackpad stops working, only USB mice work. (The laptop doesn't have a PS/2 port) I have KDE and fluxbox installed, neither of them experience the problem, so it is a problem with GNOME.

This guy seems to have the same problem:
[http://ubuntuforums.org/showthread.php?t=1567919](http://ubuntuforums.org/showthread.php?t=1567919)

But it was never resolved.

The output of xinput list shows the trackpad attached... 
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9116;   &#8627; HP Optical USB Mobile Mouse                 id=14    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
```
But it says the virtual core pointer is the master... is that a problem?

---

