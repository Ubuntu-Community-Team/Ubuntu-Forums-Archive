---
title: "Shutdown instead of reboot"
date: 2010-11-15
forum: General Help
---

### Post by Cabalbl4 on 2010-11-15
I am facing a strange problem on my ubuntu 9.10 desktop: 
When I try to reboot the system (by menu, or by sudo reboot, or by sudo shutdown -r, or by sudo init 6) it just shuts down with no reboot.

The last thing i see in the output is "will now halt". I wonder if there should be "will now reboot", but I do not know how to fix it.

Any ideas?

---

### Post by Cabalbl4 on 2010-11-16
*bump*

---

### Post by Cabalbl4 on 2010-11-16
Adding acpi=off or noacpi to grub did not solve the problem... I tried to play with bios energy settings - no luck. Reinstalling initscripts did not help (maybe I need to purge them instead of reinstall?)

---

### Post by Cabalbl4 on 2010-11-16
Resetting bios did not help. Reinstalling upstart also... anyone?

---

### Post by Cabalbl4 on 2010-11-18
The problem was fixed by clean-install of lucid. Even upgrade did not help :)

---

