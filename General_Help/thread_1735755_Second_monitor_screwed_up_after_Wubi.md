---
title: "Second monitor screwed up after Wubi"
date: 2011-04-21
forum: General Help
---

### Post by cincinnatus13 on 2011-04-21
Alright, so I installed Wubi (basically because I'm waiting for 11.04 to come out to decide if I want to fully dual boot with Windows) and I was messing with the proprietary driver from Nvidia on it trying to get it to display my second monitor correctly. I had to restart the X server a few times and I still didn't get it right. Problem is, it seems to have truly f-ed up the graphics driver or something as now the second monitor is just a mish mash of lines.
I uninstalled Wubi and no change (the monitor is messed up in Windows as well.) Installed the newest graphics drivers (no change). Uninstalled the graphics drivers completely, rebooted, cleaned out the registry with CCleaner, rebooted and installed the new drivers again (with a clean install). No change still. I have even restored Windows to an earlier point in time and it won't correctly display my second monitor.

I should mention that it DOES display a clone just fine, it's just that when I try to extend the desktop, it's all messed up. Any ideas on how to fix it? I really am at a loss considering a full reinstall of the drivers still didn't fix it. I also tried reinstalling Wubi again and fixing it from there to no avail.

Edit: After messing with Nvidia controls in Win7, I can extend it but only up to 1680x1050. Once I go to 1920x1080, it gets all f-ed up again.

---

### Post by cincinnatus13 on 2011-04-22
Edit: Problem solved. Reset all settings on the monitor. Not sure if that was what really fixed it as I messed around with a couple things in Nvidia settings, but all is back to normal now.

---

