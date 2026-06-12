---
title: "Custom mount point for droid phone?"
date: 2011-02-28
forum: General Help
---

### Post by LASTGUY2GETPS2 on 2011-02-28
When I connect my droid and enable usb storage use, ubuntu automatically mounts the SD card of my phone. Its mount point seems to be "/media/%13". If I wish to browse to that location I have to navigate to "file:///media/%13" in the nautilus bar. Typing in "/media/%13" will bring up a non existent directory error.

I guess my questions is how can I change the mount point in /media/ to something normal like "Droid"? And how can I make it such that when I navigate I don't need the "file://" prefix?

---

### Post by dcstar on 2011-02-28
> **LASTGUY2GETPS2 said:**
> When I connect my droid and enable usb storage use, ubuntu automatically mounts the SD card of my phone. Its mount point seems to be "/media/%13". If I wish to browse to that location I have to navigate to "file:///media/%13" in the nautilus bar. Typing in "/media/%13" will bring up a non existent directory error.

I guess my questions is how can I change the mount point in /media/ to something normal like "Droid"? And how can I make it such that when I navigate I don't need the "file://" prefix?

Label the partition to whatever you want and it will be mounted under that name in /media.

---

