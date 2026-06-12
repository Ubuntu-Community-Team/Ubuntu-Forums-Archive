---
title: "Headphones don't mute laptop speakers"
date: 2010-09-26
forum: General Help
---

### Post by Chris1274 on 2010-09-26
This seems to be a common issue, but I've searched in vain for a solution.

I'm on an IBM Thinkpad X60. When I plug either headphones or external speakers into the headphone jack (whether on the docking station or the laptop itself), the laptop speakers aren't muted. I can hear sound coming from both simultaneously. I've tried editing the /etc/modprobe.d/alsa-base.conf in all kinds of ways, my most recent attempt being to add the line:
```
options snd-hda-intel model=thinkpad
```but still with no success.

I'm using 10.04 with the 2.6.32 kernel. I tried installing the .34 kernel with no better results, so I switched back.

Any suggestions would be greatly appreciated.

---

### Post by Chris1274 on 2010-09-26
Interesting ...

I tried removing the laptop from th dock, after which everything worked as it should: no sound coming from speakers with headphones plugged in. Then I put the laptop back in the dock, expecting the original problem to reemerge, but it didn't. As of now, at least, there's only sound coming from the headphones/external speakers, not from the laptop speakers.

---

