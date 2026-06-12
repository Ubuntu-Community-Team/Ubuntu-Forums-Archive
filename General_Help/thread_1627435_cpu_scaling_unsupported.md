---
title: "cpu scaling unsupported?"
date: 2010-11-21
forum: General Help
---

### Post by princeofnam on 2010-11-21
I'm running a P4 HT with hyperthreading enabled in BIOS.

when I try to change my CPU frequency from the panel applet I get this error:
-
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.
-
Any ideas?

---

### Post by efflandt on 2010-11-21
Look through **dmesg | less** or /var/log/messages and compare your rated cpu speed to **grep MHz /proc/cpuinfo** when idle to see if freq scaling is happening automatically.  If the computer is always running full speed, maybe a BIOS setting needs to be changed to let the OS do that.

Note that the BIOS of some laptops may automatically throttle to a lower speed if they think they sense an inadequate (substitute?) power supply.

---

