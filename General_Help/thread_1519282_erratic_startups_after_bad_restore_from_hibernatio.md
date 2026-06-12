---
title: "erratic startups after bad restore from hibernation"
date: 2010-06-27
forum: General Help
---

### Post by oomlout on 2010-06-27
After my most recent hibernation, when I attempted to restore, something crashed and I got screens full of text instead.

Now when I try to boot, I get various behaviors, none of them good:
 - often the boot process apparently hangs after the console prints "starting xrdp"
 - sometimes I get to the standard gnome login dialog, but after choosing a username, no password box ever appears.
 - occasionally, I get the password box and enter my password, the background changes, but no desktop/windows/what-have-you ever get painted.

The last time I failed to get a password box, I logged into the console and saw the attached.  Apparently "landscape-sysin" crashed, possibly due to a missing symbol in apt-config?

Anyway, I'm not sure where to go from here.  Any help/pointers appreciated.

---

### Post by cariboo on 2010-06-28
Boot from the Live CD and once at the desktop open a terminal and type:

```
sudo fsck -a /dev/sda1
```

Substitute your partition for the one in the example above.

---

### Post by oomlout on 2010-06-29
fsck reported no problems, and behavior has not changed as a result. (I think it ran automatically on one of my many reboots, but I ran it again as you suggested to make sure)

---

