---
title: "No GUI after latest updates"
date: 2009-11-27
forum: General Help
---

### Post by n3rdyn00b on 2009-11-27
So, I've had the occasional problem running Karmic, the most annoying one being that my machine tends to lock up randomly whenever it wants (most notably while I'm surfing the Web via Firefox).  I installed all of most recent updates when prompted to by the update manager, thinking this might solve my problems.  Instead, I've lost my GUI.  When my machine boots up, I get the standard CLI login prompt, but it appears to be flickering on my screen.  Any thoughts?

---

### Post by MelDJ on 2009-11-27
try typing: sudo gnome-desktop
is it flickering so bad till it is unusable? might be graphic related

---

### Post by kio_http on 2009-11-27
You use probably an Nvidia card. Every kernel upgrade the driver should be reinstalled. I would recommend using the driver from nvidia's site.

---

### Post by 3rdalbum on 2009-11-27
> **kio_http said:**
> You use probably an Nvidia card. Every kernel upgrade the driver should be reinstalled. I would recommend using the driver from nvidia's site.

Wrong way around :-)  The driver from [www.nvidia.com](www.nvidia.com) will not stay in sync with your kernel. The driver from the Hardware Drivers program will. So it's advisable to use the driver from the Hardware Drivers program.

Boot up in recovery mode and reinstall the driver, and it might be a good idea to research how to add the Nvidia driver to the DKMS system so it will be rebuilt on every kernel upgrade.

---

### Post by n3rdyn00b on 2009-11-29
Thanks all for the replies.  The CLI is flickering to the point of being unusable (can't even log in).  I'm guessing I'll just have to go with a fresh install--again--and be more careful with my updates.

---

