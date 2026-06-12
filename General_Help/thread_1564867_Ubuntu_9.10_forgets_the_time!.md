---
title: "Ubuntu 9.10 forgets the time!"
date: 2010-08-31
forum: General Help
---

### Post by jre6 on 2010-08-31
I use Ubuntu 9.10 on my Dell Latitude D620 laptop. Over a few days, I have noticed a strange problem : Ubuntu forgets the time but the date is correct.

Please help.

---

### Post by BrandyBear on 2010-08-31
i use 10.04 at ot has a feature that says Always update time and date im not sure if its on 9.10 though

---

### Post by jre6 on 2010-08-31
No, it isn't there on Ubuntu 9.10. Checked the preferences and the right click menu.

---

### Post by BrandyBear on 2010-08-31
Hmmmmm....Peculear I have no idea on how to solve this sorry

---

### Post by jre6 on 2010-08-31
What is the version of the clock on Lucid? I am hoping to resolve the problem by updating to the latest version and then enabling the update.

Also, I had updated the kernel to 2.6.35 (that of Maverick (10.10)). Is this the source of the problem?

---

### Post by slakkie on 2010-08-31
try installing openntpd and sync your clock with an NTP server.

---

### Post by hariks0 on 2010-08-31
Not sure about laptops, but desktops have a small cell that keeps the date, time etc while it is powered off. Once in a while one has to replace that cell or the PC may reset the date to its defaults.

Hope it helps.:D

---

### Post by ilovelinux33467 on 2010-08-31
check in your system bios and see if that time is incorrect as well

---

### Post by jre6 on 2010-09-01
The time in the BIOS was correct, so I did a fresh install, which resolved the problem.

---

