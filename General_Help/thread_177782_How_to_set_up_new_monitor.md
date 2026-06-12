---
title: "How to set up new monitor?"
date: 2006-05-16
forum: General Help
---

### Post by dallas7 on 2006-05-16
I recently set up Ubuntu 5.10 on P3/866 system using a 15" NEC LCD monitor that had a max rez of 1024x768.

Now I'm running a 19" NEC AccuSync that is capable of much higher resolutions.  However, the Screen Resolution Preferences won't show anything higher than that original 1024x768.

How do I get Ubuntu to recognize this "new" monitor and some higher rez settings?

Thanks!

---

### Post by dallas7 on 2006-05-16
Oops.  Posted this one in the wrong place.  Sorry.

---

### Post by ZiLOG_Z80 on 2006-05-16
```
sudo dpkg-reconfigure xserver-xorg
```more than likely the setup will be able to detect the settings from the monitor and use the native resolution

---

