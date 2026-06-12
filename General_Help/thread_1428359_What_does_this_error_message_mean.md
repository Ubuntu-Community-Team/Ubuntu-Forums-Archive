---
title: "What does this error message mean"
date: 2010-03-12
forum: General Help
---

### Post by Fika on 2010-03-12
Using the ubuntu live cd 9.10 I get weird error messages when shutting down the system, sometimes it is this one:

device removed: /freedesktop/Hal/devices/net_80_00_60_0f_e8_00

other times it is bunch of errors saying something like:

 i/o error/end request/dev/sector ****  , with all different sector numbers..

These happens even when I have not installed anything, not using any flash drives etc...

Thanks

---

### Post by walter_j on 2010-03-12
might be hd errors

try
sudo touch /forcefsck

then reboot

---

