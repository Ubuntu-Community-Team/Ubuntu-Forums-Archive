---
title: "[radeon] VSync on both LCD and HDMI?"
date: 2012-06-06
forum: General Help
---

### Post by phibxr on 2012-06-06
I've been trying to find a solution to having both my LCD and HDMI-output (a Samsung plasma TV) being VSynced even though they are using different refresh rates.

On my ATI Radeon-card I've tried this with both the version of the proprietary drivers provided through the official Ubuntu channels for Ubuntu 12.04, the latest drivers straight from ATI, and the open source drivers.

It seems like the only way I can get it working is by running one separate X-session on each screen -- is this really a limitation of X.org or the drivers? Running one X-session with dual monitors enabled will result in one display being properly VSynced and the other one trying to sync to the other displays refresh rate.

This results in tearing on one screen, and I'll have to choose whether I'd like to have the tearing on my LCD-monitor or on the TV.

I've had the same experience using the proprietary NVidia drivers on an NVidia-card as well, and using integrated graphics from Intel, so the issue does not seem to be limited to the Radeon drivers.

This seems a bit strange since other operating systems seems to be able to handle it flawlessly.

---

### Post by beoram on 2012-08-02
Did you ever find any solution or further information on this problem?

---

