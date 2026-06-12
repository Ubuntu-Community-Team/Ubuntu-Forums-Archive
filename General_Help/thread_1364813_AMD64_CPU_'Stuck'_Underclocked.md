---
title: "AMD64 CPU 'Stuck' Underclocked"
date: 2009-12-26
forum: General Help
---

### Post by jasonditz on 2009-12-26
This problem seems to have been true since I upgraded to 9.10, but I can't figure out why it's the case. 

powernow-k8 seems to be putting my Phenom X4 9750 into "cool n' quiet" mode at 1200 Mhz on startup, but never bumps it back to 2400 Mhz no matter how heavy a load I throw at the system (I maxed them all to 100% and the system slowed to a crawl, but powernow-k8 didn't get the hint and bump it up). I was wondering why my system didn't seem as peppy since I upgraded, apparently its because my CPU cores are all "stuck" at half their normal clock speed.

Any ideas on what I can try? dmesg isn't giving me anything interesting about powernow-k8, just that it knocked it down to 1200 Mhz after boot.

---

### Post by zvacet on 2009-12-27
I don´t know if this is right answer,but did you tried to disable **cool n' quiet** from BIOS?

---

### Post by dcstar on 2009-12-27
> **jasonditz said:**
> This problem seems to have been true since I upgraded to 9.10, but I can't figure out why it's the case. 

powernow-k8 seems to be putting my Phenom X4 9750 into "cool n' quiet" mode at 1200 Mhz on startup, but never bumps it back to 2400 Mhz no matter how heavy a load I throw at the system (I maxed them all to 100% and the system slowed to a crawl, but powernow-k8 didn't get the hint and bump it up). I was wondering why my system didn't seem as peppy since I upgraded, apparently its because my CPU cores are all "stuck" at half their normal clock speed.

Any ideas on what I can try? dmesg isn't giving me anything interesting about powernow-k8, just that it knocked it down to 1200 Mhz after boot.

Add the CPU applet to a panel and try to manually change it.

It is probably an old configuration setting causing the problem, upgrades are always problematical compared to fresh installs.

---

