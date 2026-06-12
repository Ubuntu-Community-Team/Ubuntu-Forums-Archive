---
title: "'Effects could not be enabled' - using nvidia 185 driver, MacBook 5,1 (Ubuntu 9.10)"
date: 2009-11-29
forum: General Help
---

### Post by jermsie on 2009-11-29
So I installed an nvidia driver yesterday manually because none would show up in Hardware Drivers, today's a different story so I chose the recommended driver (version 185). This is currently in use but I cannot enable Normal or Extra visual effects.

Using Ubuntu 9.10 x86 - MacBook 5,1 (early 2009)

Hmmm...

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
Try uninstalling/deleting everything related to the driver and reinstalling. If that doesn't work post back.

---

### Post by jermsie on 2009-11-29
> **Sin@Sin-Sacrifice said:**
> Try uninstalling/deleting everything related to the driver and reinstalling. If that doesn't work post back.

How would I go about removing the manually installed driver, and by doing all this, will it maybe screw the system up so I can't login at all? I've had nasty things like that happen in the past. Cheers :)

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
If you installed the official nvidia drivers then the same way you installed them. Otherwise just go into synaptic and remove all things nvidia... err... whatever driver you're using. No... it should all default to vesa. Therein you just log in and install the 185 driver again. I think you have 2 drivers installed and they are conflicting each other.

---

### Post by jermsie on 2009-11-30
> **Sin@Sin-Sacrifice said:**
> If you installed the official nvidia drivers then the same way you installed them. Otherwise just go into synaptic and remove all things nvidia... err... whatever driver you're using. No... it should all default to vesa. Therein you just log in and install the 185 driver again. I think you have 2 drivers installed and they are conflicting each other.

Now both entries have a flickering login, typing is difficult as it doesnt register each press. Issue..

---

### Post by jdheron87 on 2010-01-01
Same thing just happened to me. I had to restart and while it was starting up I had to hit esc to interrupt the grub. I have ubuntu 9.1, I don't know if different versions are different, but I had an option (2nd down) to boot with the kernel in recovery mode. once you do that you have the option to boot to a root shell...
What happened was I was trying to install the ati drivers with Envyng. so when I got to the root shell, I just typed in "envyng -t" to bring up text mode, and it gives you the option to uninstall your drivers, go ahead and do that, then reboot.

Lemme know if this helps

---

