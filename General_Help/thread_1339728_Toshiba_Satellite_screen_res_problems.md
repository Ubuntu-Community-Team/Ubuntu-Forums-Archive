---
title: "Toshiba Satellite screen res problems"
date: 2009-11-27
forum: General Help
---

### Post by NovaAesa on 2009-11-27
Hi all,

I'm installing Ubuntu 9.04 on a Toshiba Satellite, and am having a few problems. Initially when I installed,  the screen resolution was set at 1024 by 768. I changed the resolution to 1280 by 800 (which is the native resolution of the screen). The problem is that whenever I have to restart the laptop, the screen resolution always reverts back to the low resolution.

The graphics chipset is an Intel Mobile 4 Series chipset, but I don't know which one. The relevant section of the output to lspci is below:

> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


If anyone knows what to do to fix this, that would be excellent. This laptop is for a new Ubuntu user =]

---

### Post by Sin@Sin-Sacrifice on 2009-11-27
Go to System>Preferences>Display and when it asks if you want to use NVIDIA settings click **NO**. It will take you to the ubuntu display manager. Set that one to the right resolution and see if it stays.

---

### Post by NovaAesa on 2009-11-28
Thanks for the help Sin, I ended up just installing Karmic and it worked fine. I guess all the bad wrap about Karmic didn't count in all cases!

---

