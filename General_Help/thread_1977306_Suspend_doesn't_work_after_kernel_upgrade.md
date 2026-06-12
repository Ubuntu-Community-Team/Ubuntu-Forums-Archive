---
title: "Suspend doesn't work after kernel upgrade"
date: 2012-05-09
forum: General Help
---

### Post by josephellengar on 2012-05-09
I'm having trouble with suspend after upgrading my kernel from 3.2.0-23-generic to 3.2.0-24-generic. With the new kernel, suspend works when I manually invoke it (press the power button and select suspend), but about 75% of the time, when I invoke suspend by closing the laptop lid, the following happens:
1) light on back of laptop screen stays on (turns off when in suspend)
2) Fan starts to work overtime, likely indicating high CPU usage
3) If I open the laptop lid back up, the screen does not turn back on
4) The only way to get the system back is to do a hard reboot (with button)

I am using an hp dv7t with a first-gen intel i7 processor, Nvidia graphics and nouveau driver. I am running a fully updated system with Gnome-Fallback mode. Suspend works completely perfectly with the 3.2.0-23-generic kernel, so I can't imagine that anything else is the cause.

Any help much appreciated.

---

### Post by josephellengar on 2012-05-09
I think that this bug is the problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994519)

---

