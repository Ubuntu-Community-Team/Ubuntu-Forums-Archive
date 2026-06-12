---
title: "Dual monitors on Maverick with ATI Radeon X600"
date: 2011-01-29
forum: General Help
---

### Post by BobPaulson on 2011-01-29
Since I upgraded from Lucid to Maverick (with latest  updates), the display with dual non-mirrored monitors does not work. I  have a Dell Dimension 9150 with 2 GB RAM, Intel Pentium 4 dual-core 3  GHz CPU and an ATI Radeon X600 graphics chip. This worked fine in Lucid and  Windows XP.

My setup: Samsung 17" SyncMaster 171s VGA 60 Hz on left, and 19"  Samsung SyncMaster 943 DVI 75 Hz on right, both at 1280 x 1024. The  Radeon controller has a VGA and a DVI socket and the two monitors are  connected as indicated. Mirrored monitors display fine. But using System  -> Monitor Preferences, uncheck "Same image in all monitors", click  on Apply, and the right-hand monitor (19" DVI) completely corrupts the  right half of the display from top to bottom.

After scouring these and other forums, I found that reducing the total screen width to less than 2048 worked, or stacking the monitors vertically.

Finally, thanks to this forum's "known Maverick issues and workarounds", I found that simply disabling Compiz (setting visual effects = none) provides a workaround.

Question: I understood from Launchpad that the general problem of total display width > 2048 was fixed? If so, why am I having this problem? Is it still in progress? Fixed with Natty?

Thanks, Bob

---

