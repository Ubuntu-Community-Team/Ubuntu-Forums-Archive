---
title: "Framebuffer and brightness adjusting problem"
date: 2010-05-24
forum: General Help
---

### Post by Dom66 on 2010-05-24
Hi,
I'm running ubuntu lucid 64 bit on my laptop and it runs perfectly, except for the plymouth splash; it shows up very late in the boot process. As i read in the FAQ, there is a workaround which is to make initramfs use the framebuffer. I tried it and it works really well, plymouth shows up all along the boot process. 

The problem is, when i tried adjusting my laptop's screen brightness, it froze completely, needing a hard reset. Same thing happens when i unplug the AC, since its supposed to dim the lights. I tried rebooting a couple of times but its always the same, and have found out it is directly related to the FRAMEBUFFER=y line added to /etc/initramfs-tools/conf.d/splash. When i remove it and run update-initramfs -u i can adjust the brightness again.

Is there a way i could make plymouth work with being able to adjust screen brightness or will i have to forget that workaround.
Thanks

---

### Post by Dom66 on 2010-05-24
bump

---

