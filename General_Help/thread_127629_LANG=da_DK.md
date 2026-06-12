---
title: "LANG=da_DK"
date: 2006-02-09
forum: General Help
---

### Post by Ragazzo on 2006-02-09
I was advised to use this shell command to get a Java applet work:
LANG=da_DK firefox

This is what I get:
(firefox-bin:7478): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

Should I install the locale somehow or?

---

### Post by hw-tph on 2006-02-09
**dpkg-reconfigure locales** 
Tick the ones you want to build and then wait until it's done. You may have to reboot too, I don't really remember.


Håkan

---

