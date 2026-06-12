---
title: "Enabling Dual Monitors with older ATI video cards"
date: 2010-10-19
forum: General Help
---

### Post by BlueTeam on 2010-10-19
Is there a simple way to have both of the monitors on a system enabled?  The video cards are both older ATI cards.  One is a Radeon 9000 AGP 64MB, and the other is quite a bit older (ATI 3D Rage Pro 2x).  When Ubuntu 10.10 is booting up, the splash screen appears nicely on the left-side monitor, and then the final desktop appears on the right-side monitor, but when I go to system --> preferences --> monitors, only one monitor is available.  I'm guessing the right monitor is fed by the Radeon (I can check if it matters).  If the splash screen appears on the left side when booting, why isn't that display available after the bootup has completed?

---

### Post by dcstar on 2010-10-20
> **BlueTeam said:**
> Is there a simple way to have both of the monitors on a system enabled?  The video cards are both older ATI cards.  One is a Radeon 9000 AGP 64MB, and the other is quite a bit older (ATI 3D Rage Pro 2x).  When Ubuntu 10.10 is booting up, the splash screen appears nicely on the left-side monitor, and then the final desktop appears on the right-side monitor, but when I go to system --> preferences --> monitors, only one monitor is available.  I'm guessing the right monitor is fed by the Radeon (I can check if it matters).  If the splash screen appears on the left side when booting, why isn't that display available after the bootup has completed?

Any Splash Screen will go to whatever the default BIOS video setting is, it has nothing to do with Ubuntu as it has not yet loaded.

Only when Ubuntu loads will it be able to use whatever supported video card it finds, some old cards have not been supported for years now.

---

