---
title: "Strange boot issue on 10.10"
date: 2011-02-01
forum: General Help
---

### Post by savaan on 2011-02-01
My wife and i were gone for the night and came back to a dead computer. Apparently we had a power outage. My comp came back up with no probs, hers gets all the way to the desktop background, but won't load any toolbars, clock, NOTHING. Just the background. We've rebooted several times but it just won't load

---

### Post by wojox on 2011-02-01
Can you Alt+F2 and type **gnome-terminal** and enter:

```
sudo touch /forcefsck
```

Then reboot and it will run a Filesystems check

---

### Post by TeoBigusGeekus on 2011-02-01
Boot up with a live cd and fsck all your drives
```
sudo fsck /dev/sda1
```
Replace sda1 with your actual partitions.
fsck will scan the drives for errors and attempt to fix them.

---

### Post by savaan on 2011-02-01
> **wojox said:**
> Can you Alt+F2 and type **gnome-terminal** and enter:

```
sudo touch /forcefsck
```

Then reboot and it will run a Filesystems check

This brought me back to the desktop and icons appeared, but no toolbars. I rebooted the comp again and its back to just the desktop background like we started with

---

