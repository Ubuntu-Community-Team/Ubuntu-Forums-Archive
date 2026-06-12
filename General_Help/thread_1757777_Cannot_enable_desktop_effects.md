---
title: "Cannot enable desktop effects"
date: 2011-05-13
forum: General Help
---

### Post by glomerulus on 2011-05-13
Hello community,

I just installed Ubuntu Lucid 64-bit on a Dell xps 15 with a Intel core  i5-2410M (sandy bridge) processor and NVIDIA GeForce GT 540M (2 gig)  gpu.

The gpu is Optimus technology enabled, and I understand that there is no optimus support for linux right now.
Hence I cannot use the NVIDIA card for display, which is fine, since I am trying to use only the intel on-chip graphics.

From a fresh install, i was not even able to change the resolution to anything other than 1024x768.
Was able to change the resolution after i upgraded the **linux-image** and **linux-headers**, though.

But i still cannot enable the desktop visual effects. Do i need to install drivers for the intel on-chip graphics?

Following the recommendations from this thread : [http://ubuntuforums.org/showthread.php?t=1739732](http://ubuntuforums.org/showthread.php?t=1739732) , i added the **xorg-edgers PPA** to my software sources, and did an **upgrade all**.
This just messed up, and i got a blank display after reboot. I had to do a fresh lucid install to fix this.

Can anyone please direct me to the correct way/drivers to install to enable desktop effects?
When i try to enable, it looks for drivers for a bit before saying **"Desktop effects could not be enabled"**

Do you think the core i5's on-chip graphics is incapable of handling even medium visual effects?

Thanks.

---

