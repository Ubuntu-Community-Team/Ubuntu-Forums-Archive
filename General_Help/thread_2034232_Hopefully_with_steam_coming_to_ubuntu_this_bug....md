---
title: "Hopefully with steam coming to ubuntu this bug..."
date: 2012-07-28
forum: General Help
---

### Post by georgelappies on 2012-07-28
... will be given some attention.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/980195](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/980195)
[http://ubuntuforums.org/showthread.php?t=1957470](http://ubuntuforums.org/showthread.php?t=1957470)


As currently it is impossible to use the proprietary ATI drivers in ubuntu 12.04 on a laptop as the 100% cpu usage from compiz when the screen goes into standby mode drains the battery in no time! :(

---

### Post by georgelappies on 2012-07-29
Would I be able to pay a compiz dev to fix this bug? And if so how much?

---

### Post by georgelappies on 2012-07-29
Found this workaround. Be sure to disable "Tearfree" as well or else it wont work:

WORKAROUND:
1. Open Catalyst Control Center.
2. Go to 3D > More Settings.
3. Set "Wait for vertical refresh" to "On, unless application specifies".
And if that doesn't work, then also do:
4. Run "ccsm"
5. In Workarounds, enable "Force full screen redraw (buffer swap) on repaint".

---

