---
title: "Repeated crashes, how do I determine the cause?"
date: 2010-09-23
forum: General Help
---

### Post by Jason Airlie on 2010-09-23
Ubuntu is repeatedly crashing on me. It seems to be Xorg crashing, but apport only reports that various apps are crashing.

The screen will go blank with a blinking dash cursor in the upper left. Then a dialog box will popup and say that xorg is running in low resolution mode. I can click ok and everything comes back up fine, but any running apps are gone.

How do I determine the cause of the crash, and hopefully eliminate it? My netbook averages 2 - 4 crashes a week.

---

### Post by jongkind on 2010-09-23
> **Jason Airlie said:**
> Ubuntu is repeatedly crashing on me. It seems to be Xorg crashing, but apport only reports that various apps are crashing.

The screen will go blank with a blinking dash cursor in the upper left. Then a dialog box will popup and say that xorg is running in low resolution mode. I can click ok and everything comes back up fine, but any running apps are gone.

How do I determine the cause of the crash, and hopefully eliminate it? My netbook averages 2 - 4 crashes a week.

You can check the entries in the "log file viewer" or alternatively examine the files in "/var/log/"

---

