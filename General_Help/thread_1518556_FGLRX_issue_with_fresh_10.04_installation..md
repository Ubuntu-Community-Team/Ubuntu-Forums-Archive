---
title: "FGLRX issue with fresh 10.04 installation."
date: 2010-06-26
forum: General Help
---

### Post by athx on 2010-06-26
Installing the proprietary ATI drivers via either: synaptic, jockey f/e, or manually provides identical results:
    When the driver 'fglrx' is used in xorg.conf, the machine will hang, completely, on trying to startx (System is entirely unresponsive, no errors, cannot switch tty, only way to use the machine again is to either power cycle, or CTRL + ALT + SYSRQ + B).
I'm a bit stumped as to why this is and haven't had much luck on IRC or in finding other people with the same problem.

The only hint I get is in the kdm log file, that complains about a bus being wrong for the card (HD 4870).

kdm log: [http://pastebin.ca/1890076](http://pastebin.ca/1890076)
xorg log: [http://pastebin.ca/1890078](http://pastebin.ca/1890078)
xorg cfg: [http://pastebin.ca/1890094](http://pastebin.ca/1890094)

Any help would be appreciated as I do need 3d acceleration.

Edit:

Identical problem with Ubuntu/gdm.

I've tried many different xorg conf files according to numerous resources regarding the matter, of which none have been successful.

If anyone has a 4870 working with a fresh 10.04 *ubuntu install, using the latest support drivers in the repository (which also happen to be the latest official drivers), please explain either how you installed/configured it or how you got past this problem.

---

