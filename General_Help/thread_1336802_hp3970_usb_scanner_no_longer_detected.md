---
title: "hp3970 usb scanner no longer detected"
date: 2009-11-24
forum: General Help
---

### Post by skralljt on 2009-11-24
When I run xsane, it says that no scanner is found.  Then when I run sane-find-scanner, it finds it.   It says it was probably detected.  I know that the 3970 is supported by sane, I read it on their website.  When I run scanimage -L, however, as the output of sane-find-scanner recommends, it says that no scanners were identified.  
Now I am really delving into some esoteric territory I don't want to be in, opening up conf files.  hp3900.conf in /usr/local/etc/sane.d/ lists the same information as does lsusb.  Everything is exactly the same.  
This is a strange error in my eyes because it was relatively painless to get my scanner working under 9.04 (by linux standards at least!)  I've tried modifying permissions in /dev/bus/usb/001 a+w, I've tried plugging the scanner into other ports, etc etc.  I've compiled sane myself from source, and compiled the hp3900 drivers from the sourceforge page and still no luck!

---

### Post by skralljt on 2010-01-02
anybody  have a working hp3970 scanner?

---

### Post by skralljt on 2010-01-02
Now it works somehow.  don't know what I did or what is different, maybe multiple reboots fixed its clock.  Or maybe it was one of the myriad updates I've installed in the intermediate months since this problem cropped up.

---

