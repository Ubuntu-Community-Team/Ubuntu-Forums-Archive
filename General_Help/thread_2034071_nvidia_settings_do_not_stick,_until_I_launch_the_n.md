---
title: "nvidia settings do not stick, until I launch the nvidia-settings tool"
date: 2012-07-27
forum: General Help
---

### Post by ant2ne on 2012-07-27
My settings which I've tweaked with nvidia-settings gui tool and/or with the .nvidia-settings.rc file do not take effect until I'm logged in and launch the nvidia-settings application. Then everything seems to snap into place. What have I done wrong?

---

### Post by mc4man on 2012-07-27
You should mention what release of Ubuntu you're using. Basically you want nvidia-settings enabled in your startup applications

(recent versions of nvidia-current install nvidia-autostart.desktop & it should be auto added to your startup apps

---

### Post by ant2ne on 2012-07-28
12.04

This theory sounds plausible as I manually installed the driver. I'm not looking to remove it and install the nvidia-current. How can I add what I need to add manually?

---

### Post by flipper T on 2012-07-28
have you got nvidia in your start up apps?

if no, add it. command should be 

```
sh -c '/usr/bin/nvidia-settings --load-config-only'
```

---

