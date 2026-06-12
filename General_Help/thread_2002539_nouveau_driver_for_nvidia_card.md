---
title: "nouveau driver for nvidia card"
date: 2012-06-12
forum: General Help
---

### Post by MoebusNet on 2012-06-12
Trying to file an ubuntu-bug for nouveau. lshw in LXterminal lists nouveau for driver. ubuntu-bug nouveau in LXterminal shows apport crash 'no such package'.

Suggestions?

---

### Post by idoitprone on 2012-06-12
> **MoebusNet said:**
> Trying to file an ubuntu-bug for nouveau. lshw in LXterminal lists nouveau for driver. ubuntu-bug nouveau in LXterminal shows apport crash 'no such package'.

Suggestions?


so what is the bug?

nouveau driver is install with the standard kernel

there nouveau driver exist as a module in your system, not a standalone package

---

### Post by MoebusNet on 2012-06-12
OK, since it is a kernel module instead of a package, how do I go about filing a bug against nouveau? nVidia is on the verge of dropping support for this video card and nouveau has not supported it since 8.10. I would like to get nouveau support for the card.

EDIT: I haven't found any easy way to do this, so I found a similar bug for Debian and added my 2 cents. Everything I've been able to find out traces nouveau back to Debian, so I guess that's where the fix will have to come from.

---

