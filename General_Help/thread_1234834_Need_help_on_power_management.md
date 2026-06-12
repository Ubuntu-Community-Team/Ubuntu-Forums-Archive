---
title: "Need help on power management"
date: 2009-08-08
forum: General Help
---

### Post by silverrope on 2009-08-08
I managed to get both ubuntu and xubuntu (9.04) running on an IBM Thinkpad A20m (Pentium III 600 Mhz, 256 MB memory, latest BIOS 1.13). Nearly everything worked (sound, wireless card, etc.) except for the power management. The gnome-power-management icon shows that laptop as AC-connected, but when I unplug the AC, it does not display the battery usage. The mouseover display continues to say that the "Computer is running on AC power". I have also the gnome panel battery monitor applet displayed and it always show 50% usage even when the battery is nearly drained or full.

Some other inconsistencies. Under the power management preferences, I set it to "Ask me" when the power button is pressed. But the laptop just powers off when I press the power button. For laptop lid closed, I set it to "Do nothing", but when I close the lid, the screen blanks out (power stays on).

Before I go on to more serious testing with suspend or hibernate, I would like to resolve these basic power issues first. Can anyone help or direct me to some info?

Thanks.

---

### Post by silverrope on 2009-08-08
I can add another anomaly related to power. On every shutdown, I get to "System halted", but the laptop does not power off by itself; I have to press the power button to completely shut it off. Bothersome, but I can live with that.

Any advice? Without the power management features to at least monitor battery use, the thinkpad effectively becomes a desktop only. Everything else about ubuntu is working fine but this. Despite the steep learning curve, I do like ubuntu, but without power management, will I be forced to go back to Windoze?

---

### Post by silverrope on 2011-08-19
Cleaning up my old thread. Solved by acpi=force. See the following:

[http://ubuntuforums.org/showthread.php?t=1235660](http://ubuntuforums.org/showthread.php?t=1235660)

---

