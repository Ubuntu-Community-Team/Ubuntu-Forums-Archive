---
title: "Dell Optiplex 960 with NVIDIA Quadro NVS 450"
date: 2010-10-05
forum: General Help
---

### Post by jaezcurra on 2010-10-05
Hi, I have just bought a Dell Optiplex 960 with a NVIDIA Quadro NVS 450.  Everything works out of the box with the 10.04.1 Live CD.  It suggests to install and activate NVIDIA proprietary drivers, but you need to restart the machine afterwards.

The problem is that, after that, all what you get is a blank screen, with not even a cursor.

The same happens when you install Lucid: blank screen with no cursor.

Ctrl+F1 does not show anything, but Ctrl+Alt+Prnt Scrn+REISUB works and the PC is reset.

In the var directory the logs show that the NVIDIA module is not loaded.

Any suggestion to fix things in the hard disk from the Live CD?

---

### Post by nevius on 2010-10-05
> **jaezcurra said:**
> Hi, I have just bought a Dell Optiplex 960 with a NVIDIA Quadro NVS 450.  Everything works out of the box with the 10.04.1 Live CD.  It suggests to install and activate NVIDIA proprietary drivers, but you need to restart the machine afterwards.

The problem is that, after that, all what you get is a blank screen, with not even a cursor.

The same happens when you install Lucid: blank screen with no cursor.

Ctrl+F1 does not show anything, but Ctrl+Alt+Prnt Scrn+REISUB works and the PC is reset.

In the var directory the logs show that the NVIDIA module is not loaded.

Any suggestion to fix things in the hard disk from the Live CD?

Try the following without a liveCD.

*Hold the shift key while the computer is booting up
*Enter the recovery mode
*edit /etc/default/grub ```
nano /etc/default/grub
``` by adding the parameter "nomodeset" to the line that reads GRUB_CMDLINE_LINUX="" so that you have a line reading like this ```
GRUB_CMDLINE_LINUX="nomodeset"
```
*Then blacklist the nouveau driver ```
nano /etc/modprobe.d/blacklist.conf
``` and add the line ```
blacklist nouveau
```

Then try rebooting your computer. If it boots up normally, de-activate and the re-activate your nvidia driver through "system --> Administration --> Hardware Drivers"

---

### Post by jaezcurra on 2010-10-05
Thank you, Nevius.  It worked!

What I did was:
   * Install 10.04.1 on the HD and reboot
   * Boot from the Live CD and use it to modify /etc/default/grub and /etc/modprobe.d/blacklist.conf on the HD
   * Remove the Live CD and boot into Recovery Mode from the HD to get a VGA Desktop
   * Install the NVIDIA proprietary drivers and ... voilà, evrything is OK now

---

