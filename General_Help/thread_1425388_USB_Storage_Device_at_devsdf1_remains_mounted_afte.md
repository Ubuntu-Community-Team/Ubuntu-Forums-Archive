---
title: "USB Storage Device at /dev/sdf1 remains mounted after removal"
date: 2010-03-09
forum: General Help
---

### Post by aeternitas on 2010-03-09
Hello,

       A while back I was working with moving some items between my SD card (connected via my mobile on a USB connection) and my system.  Initially, the SD card was identified at /dev/sdf1, mounted at /media/disk.  Somewhere along the line, things got mixed up quite badly; /dev/sdf1 is mounted at /media/B0E3-C481 and remains there after the device is disconnected.  When reconnected, it's now found at /dev/sdg1 mounting at /media/disk-1.  Is the dead mount a concern, provided there's really nothing that would attempt to write to or read from it?

---

