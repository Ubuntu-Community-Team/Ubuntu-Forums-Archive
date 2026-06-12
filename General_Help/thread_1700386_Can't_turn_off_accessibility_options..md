---
title: "Can't turn off accessibility options."
date: 2011-03-04
forum: General Help
---

### Post by ColemanK on 2011-03-04
A friend of mine decided it would be funny to turn on all the accessibility options at the login screen on my install of Ubuntu Netbook Remix. Because the screen's so small, half of the screen is used for magnification. The half of the screen that is now completely useless, is the half of the screen that has the accessibility options on it. 
I can't change them back.
So I'm wondering if there's a way to disable them from the command prompt or something. I've tried the failsafe graphics, and they're even worse.

Thanks in advance.

---

### Post by Krytarik on 2011-03-05
Run this command to turn of the magnifier:
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```

---

### Post by ColemanK on 2011-03-05
Worked like a charm. Thanks!

---

