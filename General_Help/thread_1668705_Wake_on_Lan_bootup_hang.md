---
title: "Wake on Lan bootup hang"
date: 2011-01-16
forum: General Help
---

### Post by josepaul on 2011-01-16
This is more of a help thread than anything, I was about to post up a thread asking why my computer hangs when I changed it to wake on lan.

It showed this ; 

**PXE-E53: No boot filename recieved**

and the computer just hanged there.

**Solution:**

When I turned on wake on lan, the BIOS automatically changed the boot sequence so that the network is the first boot option. Simply change it back (or disable network boot) from the BIOS. Problem solved.

---

