---
title: "GDM Trouble?"
date: 2009-09-16
forum: General Help
---

### Post by popejeremy on 2009-09-16
Hi, I just turned on my EEE 1005HA running Ubuntu karmic (development branch) and it puked at me. GDM doesn't want to start. This seems to be the key error:

```
init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```

I also find these lines (among many others) in my /var/log/Xord.0.log:

```
(EE) intel(0): Failed to initialize kernel memory manager

(EE) intel(0): AGP GART support is either not available or cannot be used.
    Make sure your kernel has agpgart support or has the agpgart module loaded.

(II) intel(0): Tiled allocation failed.

(EE) intel(0): Couldn't allocate video memory.

Fatal server error:
AddScreen/ScreenInit failed for driver 0

```


Now what do I do?

---

### Post by P4man on 2009-09-17
you could post it in the appropriate forum:
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

You may also see some posts there about that same issue

---

