---
title: "OpenOffice 3.1 anti-aliased fonts?"
date: 2009-07-04
forum: General Help
---

### Post by eyeprotocol on 2009-07-04
Hello all

I installed Kubuntu 9.04, configured it perfectly etc.
Then i decided to install OpenOffice. To my surprise, the default OOffice in the repositories also installs pulseaudio, which i wouldn't have. So i downloaded the proper deb files for the OO home site, installed it - all OK, except that i do not have anti-aliased fonts, not in the OO menus, not in any of the OO applications.

Any ideas?

Panos

---

### Post by Soul-Sing on 2009-07-04
```
sudo dpkg-reconfigure fontconfig-config
``` then select "Autohinter", "Always" (for subpixel rendering on LCD display), and "No" for Enable bitmapped fonts. Then, change in System/Preferences/Appearance/Fonts to "Subpixel" smoothing.

---

### Post by eyeprotocol on 2009-07-04
These steps have been taken. Anti-aliasing is present in all of my KDE environment. Only OpenOffice lacks the feature.

---

### Post by Soul-Sing on 2009-07-04
Found this: [http://www.openoffice.org/dev_docs/features/3.1/index.html#r1.1](http://www.openoffice.org/dev_docs/features/3.1/index.html#r1.1)

===> [http://blogs.sun.com/GullFOSS/entry/finally_anti_aliasing_is_done](http://blogs.sun.com/GullFOSS/entry/finally_anti_aliasing_is_done)

---

