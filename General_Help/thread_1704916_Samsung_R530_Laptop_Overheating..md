---
title: "Samsung R530 Laptop Overheating."
date: 2011-03-11
forum: General Help
---

### Post by Eneco on 2011-03-11
My Samsung R530 laptop is over heating, I believe it is the fan because I can't feel it working at all. When it over heats it just shutsdown...

A few times it is came up with a warning while shutting down for a split second saying a extremely high temperature and shutting down seconds later. (Can't remember what it says exactly).

I am running Ubuntu 10.10 with Nvidia Geforce with Cuda. I have tried reinstalling Ubuntu, installing Fedora... Nothing I have tried has worked. :(


Is there anyway at all to change the fan speed? Something?! I am getting really frustrated...! :confused:


Eneco.

---

### Post by Eneco on 2011-03-12
Anyone help please?

---

### Post by SteveDee on 2011-03-12
> **Eneco said:**
> My Samsung R530 laptop is over heating, I believe it is the fan because I can't feel it working at all....

If you think this is a Linux related problem, try the fix on Post#8 here: [http://ubuntuforums.org/showthread.php?t=1677339](http://ubuntuforums.org/showthread.php?t=1677339)

But if the fan does not work when you just boot into BIOS...you may need a new fan!

---

### Post by Eneco on 2011-03-12
*Meant To Quote*

---

### Post by Eneco on 2011-03-12
> **SteveDee said:**
> If you think this is a Linux related problem, try the fix on Post#8 here: [http://ubuntuforums.org/showthread.php?t=1677339](http://ubuntuforums.org/showthread.php?t=1677339)

But if the fan does not work when you just boot into BIOS...you may need a new fan!

I tried what you suggested and I'm not sure if it did anything because it started working after I tweaked the BIOS settings. I changed a setting which it suggested changing if using a Unix OS. I tried your tweak after I changed the BIOS settings.

I will mark this as solved after I confirm that it is working 100%. :)

---

### Post by Eneco on 2011-03-12
When in the BIOS the fan works much better. But when in Ubuntu it is much weaker...

Going to into the BIOS then restarting going into Ubuntu causes Ubuntu to have the BIOS' fan speed. Is there anyway to max the speed of the fan in Ubuntu? :frown:

---

### Post by SteveDee on 2011-03-12
> **Eneco said:**
> When in the BIOS the fan works much better. But when in Ubuntu it is much weaker...


Some BIOS run in a sort of fail-safe mode, where the cpu runs at full speed until its told to slow down by the OS.

Originally you said the fan was not running under Ubuntu. If its running now, it may be at the correct speed for the current cpu temperature. You could try and load the cpu to 100% (maybe by running a profiler or benchtest app) and see if it will speed up as the cpu gets hotter.

You could try lm-sensors to monitor fan & cpu temperatures, but this app may not work with your hardware (search for it in Synaptic and give it a try anyway!).

> Going to into the BIOS then restarting going into Ubuntu causes Ubuntu to have the BIOS' fan speed. Is there anyway to max the speed of the fan in Ubuntu?

There are apps like thinkfan and fancontrol (again, search Synaptic) but its pot luck as to whether they work on your hardware.

---

