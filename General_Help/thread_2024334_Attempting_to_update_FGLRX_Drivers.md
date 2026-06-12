---
title: "Attempting to update FGLRX Drivers"
date: 2012-07-13
forum: General Help
---

### Post by Dannihaag on 2012-07-13
I recently installed Ubuntu  12.04 64bit and I have worked for hours today trying to figure out how to update my drivers. First I went to additional drivers, and had an error installing the "ATI/AMD proprietary FGLRX graphics driver (post-release updates)"

So I decided to try and get Catalyst, but i couldn't manually install drivers because I couldn't override the old drivers, and I couldn't remove them. 

So now I am back to additional drivers, and the error I am getting is this:
2012-07-12 16:31:54,938 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2d1b2d8>
2012-07-12 16:31:57,630 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-07-12 16:31:57,807 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-12 16:31:57,809 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-12 16:31:57,885 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-12 16:31:57,919 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-12 16:31:57,945 DEBUG: Software modem not available
2012-07-12 16:31:57,945 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-12 16:31:57,989 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

I have no idea what any of this means, but if anyone could shed some light on the topic and walk me through how to fix this so I can actually play Minecraft. (getting the black screen error)

---

### Post by QIII on 2012-07-13
The fglrx-updates and fglrx-amdcccle-updates packages sometimes do not work.  Using the graphical "Additional Drivers" method sometimes does not work.

Bear in mind that the fglrx driver in the repo IS the official AMD/ATI driver current at the time of the Ubuntu final release, in this case 12.4.  Unless there is some urgent need for Catalyst 12.6, 12.4 should suffice.

I would try this:

```
sudo apt-get remove --purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

If you couldn't install from the AMD source package, there is probably nothing to worry about there.

If you do not have Intel/ATI hybrid graphics or ATI/ATI hybrid graphics, visit the ATI wiki in my signature and look for the section titled something like "Alternate command line method with hardware acceleration".

If you have hybrid graphics, I'm still working on that and will add it to the wiki when I am sure I have a good answer.

---

