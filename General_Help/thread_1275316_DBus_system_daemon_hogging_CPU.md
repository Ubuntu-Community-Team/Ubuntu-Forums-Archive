---
title: "DBus system daemon hogging CPU"
date: 2009-09-25
forum: General Help
---

### Post by TheCelloFellow on 2009-09-25
Occasionally my DBus system daemon will start to hog about 30% of the CPU. It does it without any trigger that I can determine, though it only does it when GNOME is running (sometimes I get sick of it and run LXDE instead and though the system daemon is still running when I do that it doesn't start to go nuts).

I've attached a dump of a few seconds of output from [FONT="Courier New"]dbus-monitor --system[/FONT]. As you can see in the attachment that from just a few seconds more than a thousand messages are sent through the dbus-daemon by dbus itself, which is obviously going to hog some CPU.

Any clues as to what is causing this would be much appreciated.

-Josh

---

### Post by TheCelloFellow on 2009-09-26
Bump

---

### Post by TheCelloFellow on 2009-09-28
Bump again.

---

### Post by monstara on 2011-04-30
I started experiencing this after upgrade to Natty. DBus daemon goes to 68% CPU usage.

---

