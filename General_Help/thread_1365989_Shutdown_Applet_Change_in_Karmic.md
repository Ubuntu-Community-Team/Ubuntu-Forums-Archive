---
title: "Shutdown Applet Change in Karmic?"
date: 2009-12-27
forum: General Help
---

### Post by landersohn on 2009-12-27
it appears to me, Karmic changed the shutdown applet a bit. In Jaunty I had one applet which let me shut down, reboot, logout, lock the screen or switch users.
Under Karmic I need to run 3 applets: ShutDown only lets you power down, rebooy or hibernate, Fast user switcher lets you lock the screen and the logout-applet lets yout logout.
Does anybody know how to get back to the jaunty behavior ?

note: I did try to install LXDE, didn't like it and removed it. It is possible that the changes to the applets are related to LXDE (I didn't keep very good notes)
Any ideas which packages to re-install if LXDE messed anything up?

---

### Post by marshmallow1304 on 2009-12-27
The thing you need to add is Indicator Applet Session.  It threw me off the first time as well.

---

### Post by landersohn on 2009-12-28
Thanks, that did the trick

---

