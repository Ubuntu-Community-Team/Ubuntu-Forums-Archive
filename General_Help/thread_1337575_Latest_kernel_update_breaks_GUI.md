---
title: "Latest kernel update breaks GUI"
date: 2009-11-25
forum: General Help
---

### Post by nomopofomo on 2009-11-25
If I choose the latest kernel from GRUB during boot I get a blinking terminal screen.

Is this a driver issue? I have the latest NVIDIA drivers installed i.e. not from synaptic.

---

### Post by Brandon Williams on 2009-11-26
Did you rebuild and reinstall the Nvidia drivers for the new kernel? When you use custom kernel modules, this will be a standard part of any kernel upgrade. After booting into the new kernel, use Ctrl+Alt+F1 to switch to a console, login, and then rebuild/reinstall the non-standard modules. Then reboot and it should work.

---

