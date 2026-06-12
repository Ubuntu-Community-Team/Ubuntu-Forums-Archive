---
title: "Ubuntu 11.10 showing purple screen during boot"
date: 2011-11-01
forum: General Help
---

### Post by emilegd on 2011-11-01
Hi,

I did a fresh install of Ubuntu 11.10 on a Toshiba NB305 netbook (with Intel GMA 3150 IGP) using the Live version on a USB flash drive.

When I start my netbook, I get a purple screen for about 5-6 minutes, then the Ubuntu loading screen for 15 seconds and then the login screen. After startup, everything seems to run fine. I get the Unity 3D desktop, wi-fi works, webcam works, etc. It was booting fine when I was using the Live distribution (about 1 min from BIOS to login screen).

I tried to boot with the grub parameters "quiet splash noapic". I also tried "nomodeset". But it did not seem to help at all.

The last thing I tried was to replace "quiet splash" with "text" instead. Now I see that it get stuck to (during boot) :
Begin : Running /scripts/init-bottom ... done

Is there a solution to this problem?

Thank you

Edit : I have the problem since installation but I updated all the packages, just to be sure it wouldn't solve the problem.

---

### Post by emilegd on 2011-11-02
I tried what papopapo76 said in another thread and it worked.

> **papopapo76 said:**
> In my case, I change the SATA setting in the  BIOS from ACHI to "Compatibility Mode" and it fixed the problem. Now the  Ubuntu start very fast. I hope this help.

---

