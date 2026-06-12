---
title: "MSI Wind12 Battery Issue? Different from known issue."
date: 2010-06-29
forum: General Help
---

### Post by BlazinNightSkye on 2010-06-29
Hi,

Just recently bought the newer MSI Wind12 U230, running ubuntu 10.04 as a wubi install next to Win 7.  I read from the known problems page that 10.04 on MSI Winds have an issue with turning off once unplugged from its power source. I don't quite have that issue. When i unplug it tells me my computer will go to hibernate in 2 minutes because the battery is low, even when it is fully charged. But after i press 'ok' or 'cancel' nothing ever ends up happening. Its more of an annoyance really. If anyone knows a fix for this it would be greatly appreciated. 
Thanks!

---

### Post by mikewhatever on 2010-06-30
Try opening gconf-editor, then navigate to /apps/gnome-power-manager/thresholds, and check the thresholds. Does something look odd?

---

