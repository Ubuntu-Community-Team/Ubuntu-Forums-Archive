---
title: "synaptic touchpad question... Xfree86 or xorg driver... which is better"
date: 2006-02-14
forum: General Help
---

### Post by hyperpsyched on 2006-02-14
Ii am running a synaptics pad with ksynaptics and still get wonky behaviour. My sensitivity is set to the lowest spot and it still opens everything when I just brush the pad...

I am running the xorg driver and was wondering if anyone was having better luck with the XFree86 driver...

---

### Post by byen on 2006-02-14
well...I had similar issues too and I tried installing gsynaptics and tried doing what you did too. It still acts up! Sometimes I feel like the cursor repostitions itself if I even look at it :cry:  but in anycase.. as it got really annoying I had to disable tapping.
If you are interested, you can do this by 
terminal>type>sudo gedit /etc/X11/xorg.conf
go to>Input Device / or wherever your mouse section is and add the following
```
Option "MaxTapTime" "0"
```

Not much ..but it might help!
Goodluck!

---

### Post by FlakJacket on 2006-02-14
My Synaptic pad has a disable button above it (hp standard i believe).  So i turn it off when I type or else it goes crazy.

Flak

---

