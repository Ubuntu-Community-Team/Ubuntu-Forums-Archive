---
title: "3 Months in Ubuntu 11.10 Upgraded to 12.04"
date: 2012-08-17
forum: General Help
---

### Post by kikert02 on 2012-08-17
After I Upgrade My Ubuntu 11.10 to 12.04 im Facing Problems like:
Frequency out of range.
CRTC MODES 64.
Resolution Is 640x480..:confused:

What Should I Do?

I have Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04).
And What Driver should i Install?..:confused:

---

### Post by sakamoto on 2012-08-20
do a fresh install instead of upgrade?

---

### Post by euphoric_anomaly on 2012-08-20
I have the dreaded Intel 945G onboard graphics and I finally got Ubuntu 12.04 to recognize my graphics driver yesterday.

This did the trick for me. MESA-UTILS
sudo apt-get install mesa-utils

Good Luck

**Note: I still have to manually change my resolution via xrandr everytime I log in.

---

