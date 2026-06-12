---
title: "Ubuntu 9.10 - screen resolution artefact's"
date: 2012-05-15
forum: General Help
---

### Post by Gorlist on 2012-05-15
Hi, ive got POS computer which ive transfered over to a laptop. The system runs Ubuntu 9.10, ive Gparted a clone of the partition from the old now defunct system to a rather aged laptop as an temporary replacement. Boots and runs fine however the screen resolution is 1600 x 1200, displayed okay unfortunately most of the desktop is outside of the monitor (so I can't see the right and lower sections of the screen space).

If I lower the resolution to something more suiting such as 1024 x 768 I get horrible stretched artefact's and have to wait for it to revert settings. Only 1600 x 1200 displays, every other lower value doesn't work. Unknown monitor/LCD withing the screen size adjuster.

The laptop is running an old Unichrome onboard graphics system.

Any help much appreciated! running out of time!

---

### Post by ajgreeny on 2012-05-15
Did the "old" OS system that you have cloned have a /etc/X11/xorg.conf file, and if so what was it?

Let's see the output of ```
cat /etc/X11/xorg.conf
``` to see if one exists, and if so what it contains.

---

### Post by Gorlist on 2012-05-15
there is no xorg.conf

and i can't drop out of GDM as i get no screen output if I close the desktop manager (just goes squiggly lines) if I try to use Xorg -configure

---

### Post by Gorlist on 2012-05-15
Fixed thanks to this thread:

Fujitsi Siemens Amilo Pro v2030
[http://ubuntuforums.org/showthread.php?p=8637517](http://ubuntuforums.org/showthread.php?p=8637517)

---

