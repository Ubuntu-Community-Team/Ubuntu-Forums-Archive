---
title: "System won't boot after upgrade to 11.04"
date: 2011-05-05
forum: General Help
---

### Post by sabersong on 2011-05-05
I just finished upgrading from 10.10 to 11.04 and restarted my system. It had been working fine, but now, after the POST test, the screen goes black, then a box floats around the monitor saying "Input Not Support." Pressing CTRL+ALT+DEL reboots the system to the POST screen, then the same thing happens. No hard drive activity, no boot, nothing. I really don't want to lose everything on my hard drive with a fresh install. Any suggestions?

EDIT: My system, a Compaq Presario, has diagnostics, so I ran that at startup, and it says I have no active partitions.

---

### Post by bergfly on 2011-05-06
Sounds like your graphics cards is not detecting the range of the monitor and not pushing valid input to it. Kubuntu is probably running, just not displaying.

First thing I would try it Alt+Ctrl+F2 Give the machine a full minute to boot, then try this.

this should bring up a command line prompt. Also, if you have a different display or a DVI cable or VGA cable alternative, you could try using those to get in and reconfigure the display driver.

---

