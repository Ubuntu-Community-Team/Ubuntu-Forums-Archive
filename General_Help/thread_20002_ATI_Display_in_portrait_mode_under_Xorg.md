---
title: "ATI: Display in portrait mode under Xorg?"
date: 2005-03-14
forum: General Help
---

### Post by pantulis on 2005-03-14
Is it possible to run a display in portrait mode under Xorg?  I'm running the latest Hoary, with the stock radeon driver, and tried ATI's propietary fglrx drivers, to no avail.  XRANDR always seems to not allow any display rotation -but keeps allowing me to change the screen resolution, though. 

 Any clues appreciated.

---

### Post by WhiteZ on 2006-01-18
Same problem here, everything else but this works with ATI drivers.

---

### Post by fif on 2006-02-05
Same problem for me. I added following lines in my Device section of xorg.conf

```

Option          "RandRRotation"
Option          "RandRReflection"

```

but got the following in the logs after having restarted the X server.

```

(WW) RADEON(0): Option "RandRRotation" is not used
(WW) RADEON(0): Option "RandRReflection" is not used
(II) RADEON(0): Direct rendering disabled

```
Seems ATI was not a good choice for this :neutral: (at least seems to me that this option is not supported).

---

