---
title: "USB Memory Adapter Doesn't Stay Mounted"
date: 2009-08-31
forum: General Help
---

### Post by michaeldelorenzo on 2009-08-31
I have an Olympus MAUSB-500 memory adapter that won't stay mounted.  I'm running Ubuntu 9.04.  The drive will mount and I'll be prompted with how I want to open the drive and I'll even be able to view the files on the drive (XD) but after a minute or so the drive will 'unmount' and I won't be able to access anything on it.

The process will repeat over and over.

What could possibly be the cause?

---

### Post by P4man on 2009-09-01
Does it still show up in

```
lsusb
```

after it "unmounts"?

If it doesnt, then its an USB issue, possibly a bad cable, USB port or device. Try connecting it to another USB port

If its still there, then maybe something is wrong with the memory card? Have you checked it for errors?

---

