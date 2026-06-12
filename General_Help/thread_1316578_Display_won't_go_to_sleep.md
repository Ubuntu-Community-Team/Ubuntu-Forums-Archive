---
title: "Display won't go to sleep"
date: 2009-11-06
forum: General Help
---

### Post by taavi on 2009-11-06
This problem is been up very long -- my displays won't go to sleep. I use dualhead desktop (radeon driver), both displays are LCDs and connected with DVI.

I put under *Screensaver Preferences -> Power Management -> On AC Power -> Display -> Put display to sleep when inactive for: 1 min* -- to test this out, displays won't go to sleep, when I'm inactive.

---

### Post by taavi on 2009-11-19
How can I solve this?

---

### Post by autonomy on 2010-04-04
I have the same problem. I have the Nvidia proprietary driver that Ubuntu automatically installed.

This seemed to work at least once: ```
xset dpms 300
```It didn't work right away after waiting a minute, but the next morning, I turned on my computer, walked away, came back and the display had gone to sleep!

After it didn't work, I think I actually entered it again without the 300. This might be a good idea with a plus before the d.

I woke up to find my Electric Sheep still running, so my screen never went to sleep.

---

