---
title: "Bluetooth config files location"
date: 2012-02-29
forum: General Help
---

### Post by Alex_L33 on 2012-02-29
Does anybody know where bluez and/or bluetooth-applet saves the configuration files relative to devices that have been paired using the GUI?

I was expecting something in ~/.config but I can't see anything useful.

I have been getting in a tangle with my bluetooth mouse recently where the mouse seems to think it is still paired (and keeps requesting access to the mouse service - no difference whether I grant or reject normally), but ubuntu thinks it is NOT still paired as I have removed it in order to try and set it up again.

Thus when I try to re-pair usually fails.

I would like to just purge all the settings and set it up again from scratch but I can't for the life of me find the files

locate bluetooth | grep home

only shows a few files and deleting them does not seem to clear the  paired devices

locate bluez | grep home returns nothing

(sudo /etc/init.d/bluetooth restart also never works in this situation - I always silently fails and I have to reboot)

---

### Post by Tiganjero on 2012-02-29
As I've never used bluetooth devices on Ubuntu, I don't have a clue as to where the files you need could be located. However, the first thing that pops to mind is purging all of the bluetooth related packages and re-installing bluez. The idea would be to execute *sudo apt-get purge <packages>*, so using *dpkg -l | fgrep blue* would help finding them. I hope that this will, in lack of a better solution (for now), help you solve this problem.

Cheers,
George

---

### Post by Alex_L33 on 2012-03-01
> **Tiganjero said:**
> As I've never used bluetooth devices on Ubuntu, I don't have a clue as to where the files you need could be located. However, the first thing that pops to mind is purging all of the bluetooth related packages and re-installing bluez. The idea would be to execute *sudo apt-get purge <packages>*, so using *dpkg -l | fgrep blue* would help finding them. I hope that this will, in lack of a better solution (for now), help you solve this problem.

Cheers,
George

Unfortunately this doesn't purge the mystery file containing the list of purged  devices (presumably it is created after install) so the problem persists. The relevant file is definitely NOT in ~/.config/ or ~/.gconf as I have tried re-naming both of those.

Its also a bit silly that bluetooth-applet segfaults when you do sudo service bluetooth restart

---

### Post by Shwan.c on 2013-04-29
some are in /var/lib/bluetooth/

---

