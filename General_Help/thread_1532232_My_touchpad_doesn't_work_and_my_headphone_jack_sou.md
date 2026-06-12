---
title: "My touchpad doesn't work and my headphone jack sounds horrible"
date: 2010-07-16
forum: General Help
---

### Post by rs87424 on 2010-07-16
I have ubuntu lucid on my acer aspire 4810tz and I have most everything working on it except for a few issues with the headphone jack sound as well as my touchpad not working.  Here is the thing though... I found out how to fix my touchpad using this command:
```
sudo modprobe -r psmouse
      sudo modprobe psmouse
```  This seemed to fix my problem except I used another command to try to fix my headphone jack problem but this is what happens when I try to enter the mouse fix ```
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
```  So it seems both of these issues are connected in some way and I can't seem to fix both of them permanently... I need some help with this problem for sure

---

