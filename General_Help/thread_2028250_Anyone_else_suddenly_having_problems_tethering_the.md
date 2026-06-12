---
title: "Anyone else suddenly having problems tethering their Android or smartphone to 12.04?"
date: 2012-07-17
forum: General Help
---

### Post by Kurtosis on 2012-07-17
I've been USB tethering with my Nexus S for over a year with no problems.  Went on vacation last week, came back, and discovered tethering no longer works.

The phone actually thinks its tethered just fine and shows the tethering icon in the top menu bar as normal.  But Ubuntu's connection icon in the top right sys tray just sits there spinning, unable to complete the connection.

I also tried Wireless Hotspot and Bluetooth, but neither seems to work either (Hotspot has always worked in the past, never tried Bluetooth tethering till today).  Normal wireless routers (home, library, starbucks, etc.) still work fine, it's just connecting to my phone that appears broken.

No idea what's the problem, a recent update maybe?

---

### Post by techvish81 on 2012-07-18
it could be a kernel update. try to boot with an old kernel, hold 'shift' while booting and select previous linux version.
see if it helps.

---

### Post by Kurtosis on 2012-07-18
You nailed it.  I reverted from 3.2.0-26-generic to 3.2.0-25-generic and it works fine.  Thanks so much.

I should report this as a regression to bugs.launchpad.net, but I'm not sure which package to reference.  Any idea which package is responsible for tethering?

---

