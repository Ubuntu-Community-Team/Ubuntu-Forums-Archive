---
title: "cpu changed or cpu ratio changed"
date: 2011-04-21
forum: General Help
---

### Post by Maxiejoe on 2011-04-21
Replaced CPU,Intel  p4, 2.3, and when restarted got the message cpu changed or cpu ratio changed  please re-enter CPU settings in CMOS and save. I re-set time, date and it is holding,  everything running ok but still get the message at log in,

How do I correct this?  Thanks in advance.

Using Ubuntu 10.10

---

### Post by dino99 on 2011-04-21
is that a big deal ?

sudo dpkg --configure -phigh -a

---

### Post by dandnsmith on 2011-04-21
> **Maxiejoe said:**
> Replaced CPU,Intel  p4, 2.3, and when restarted got the message cpu changed or cpu ratio changed  please re-enter CPU settings in CMOS and save. I re-set time, date and it is holding,  everything running ok but still get the message at log in,

How do I correct this?  Thanks in advance.

Using Ubuntu 10.10

You need to get into the BIOS settings screen(s) at bootup (using Del, F11 or whatever works for your BIOS), and go through the speed of CPU settings to get them aligned with the current CPU. Once you've saved the (new) settings, you should be able to boot without further messages.

HTH

---

