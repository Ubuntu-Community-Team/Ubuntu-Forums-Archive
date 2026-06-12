---
title: "Hibernation/suspend doesn't work"
date: 2011-01-24
forum: General Help
---

### Post by gunnarflax on 2011-01-24
I can't suspend my PC. When I try to hibernate the screen goes black and then it locks so I have to log in again. During the attempted hibernation a message flicker which I got from dmesg:

```
[   57.197853] Suspending console(s) (use no_console_suspend to debug)
[   57.220854] pm_op(): usb_dev_freeze+0x0/0x20 returns -2
[   57.220857] PM: Device usb8 failed to freeze async: error -2
[   57.246876] PM: restore of devices complete after 0.314 msecs
```I'm running a fully updated maverick x64 distribution.

might just add that this is a HTPC with a iMON LCD and IR-receiver which uses an internal usb-port.

How do I fix this error?

---

### Post by gunnarflax on 2011-01-24
bump*

---

