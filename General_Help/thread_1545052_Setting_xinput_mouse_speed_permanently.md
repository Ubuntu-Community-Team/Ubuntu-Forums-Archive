---
title: "Setting xinput mouse speed permanently"
date: 2010-08-03
forum: General Help
---

### Post by M4he on 2010-08-03
Hi Ubuntu community,

My mouse has high dpi and is too fast even on lowest speed and acceleration settings.
To fix this I always run the following command via the terminal:
```
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 2
```Is it possible to set this permanently? I already tried running a .sh script on startup via autostart with the command in it but that didn't work...

Thanks in advance!

---

### Post by M4he on 2010-08-06
Silly me...
I forgot to set the .sh script to executable -.- It's working now with autostart.

---

