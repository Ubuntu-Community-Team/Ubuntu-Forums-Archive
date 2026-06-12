---
title: "USB flash drive problem"
date: 2011-06-17
forum: General Help
---

### Post by Anachronox on 2011-06-17
I installed 11.04 on a laptop I recently acquired second-hand. Everything is fine except I can't access my flash drive. My iPod is recognized but not this drive. I can see the drive when I do the lsusb command but it doesn't show up in the Computer window anywhere. This drive works on my desktop install of 11.04. Anyone know what this is about? It's a 1 GB PNY Attache, if that's relevant.

---

### Post by DirtyPC on 2011-06-17
change usb port, or plug and unplug.

Then run sudo fdisk -l

---

### Post by Anachronox on 2011-06-17
There's only two USB ports, I already tried both of them. I think I can see it in fdisk, /dev/sdb1. Do you need to see the output?

Edit: OK, I mounted it manually but how can I get it to do it automatically like it should?

---

