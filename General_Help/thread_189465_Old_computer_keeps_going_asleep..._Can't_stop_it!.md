---
title: "Old computer keeps going asleep... Can't stop it!"
date: 2006-06-05
forum: General Help
---

### Post by Mamour on 2006-06-05
Hi all,

I'm having a very annoying problem. I installed 6.06 on an old computer (HP Vectra corporate PC, running on a Celeron 466MHz), and all seemed to go well. Nevertheless, I've hit a very problematic issue. I'm using said computer as a printer server, so it needs to be running at all times. Under breezy, I had no problems; however, with my recent upgrade to dapper, the computer keeps going asleep (or in standby mode?) when it's unused for something like 10 minutes.

I have found no way to stop this behaviour. I've tried pulling all the sliders in Power Management to their max, as well as stopping acpi-support, but none of these had any effect whatsoever.

Is there any way to stop this from happening, for real?

Thanks in advance,

---

### Post by _simon_ on 2006-06-05
Try this...

from terminal: gconf-editor

Go to apps -> gnome-power-manager and check your settings in there.

---

### Post by flar on 2006-06-05
If killing gnome-power-manager doesn't work, maybe you can disable any power management options in the bios

---

### Post by Mamour on 2006-06-05
Indeed... The BIOS was set to suspend the computer after 15 minutes of inactivity. I never noticed this however, as breezy seemed to disregard this setting.

Anyway, problem solved, I changed the BIOS setting, and I'm set. Thanks for your help!

---

