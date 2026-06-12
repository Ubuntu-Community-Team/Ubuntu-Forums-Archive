---
title: "I can't repair Video Drivers"
date: 2009-09-04
forum: General Help
---

### Post by Smando on 2009-09-04
Well, yesterday I installed ATI drivers from Synaptic, only for curiosity. But when I reboot my PC appears Loading Ubuntu Logo, and after that the screen flashes and doesn't start.
I tried to put the next in recovery mode: 
```
sudo dpkg -reconfigure xserver-xorg
```
But the problem is not resolved. I need some help please.

---

### Post by Nepherte on 2009-09-04
To figure out what the problem might be, see /var/log/Xorg.0.log. Look for errors in particular (EE).

```
cat /var/log/Xorg.0.log
``` or
```
cat /var/log/Xorg.0.log || grep EE
``` to look for errors in particular.

---

### Post by Johnny B on 2009-09-04
boot the recovery mode and:
# sudo apt-get remove xorg-driver-fglrx 

reboot to desktop and try installing the driver with envy-ng

---

### Post by Smando on 2009-09-04
Hi I tried with:
```
cat /var/log/Xorg.0.log
```But nothing happened.
 
And I sucefully uninstall video drivers. Now only start in console mode. And when I looked for ATI drivers from Envy, only appears 1 option, I selected it and only start in console mode.

Yep, It only starts in text mode.

---

