---
title: "Ubuntu Low Graphics Issue"
date: 2011-04-05
forum: General Help
---

### Post by nully_cwc on 2011-04-05
Hi,
 
I am a complete newbie to ubuntu so forgive me if I ask a silly question or am in the wrong place.
 
My laptop has crashed since yesterday and now when booting it comes up with an error saying Ubuntu is running in low graphics mode.
 
(EE) RADEON (0): [DRM] failed to set drm interface version
(EE) RADEON (0): Kernel modesetting setup failed
(EE) Screen(s) found, but none have usable configuration.
 
I then hit okay and it gives me options but the only one that works is exit to console login.
 
Please help! Thanks

---

### Post by nully_cwc on 2011-04-05
Can anyone help?

---

### Post by 3Miro on 2011-04-05
From the low graphics mode, go to System -> Admin -> Additional Drivers. 

1. Uninstall whatever ATI drivers you have installed. 
2. Reboot.
3. Install the drivers again.
4. Reboot.

This should be the easiest way to reinstall the driver and everything should work fine.

If you have a Radeon 4xxx or newer, the I suggest you don't bother with the additional drivers at all. The default ATI deriver is pretty good now.

---

