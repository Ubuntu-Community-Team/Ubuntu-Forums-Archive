---
title: "dontzap in natty"
date: 2011-05-14
forum: General Help
---

### Post by reuben on 2011-05-14
How do I install dontzap in natty? (It's not in the repositories.) Or, is there an alternative now?

---

### Post by VCoolio on 2011-05-14
You should learn the new default in X.org (well, not that new, and it's a kernel thing), which is alt+[sysrq](http://en.wikipedia.org/wiki/Magic_SysRq_key)+k. Sysrq = printscreen. Or add this to /etc/X11/xorg.conf (create the file if necessary): ```
Section "ServerFlags"
        Option          "DontZap"               "false"
EndSection
```

---

### Post by kostkon on 2011-05-14
The option to enable or disable CTRL+ALT+BACKSPACE is now in your keyboard preferences.

---

