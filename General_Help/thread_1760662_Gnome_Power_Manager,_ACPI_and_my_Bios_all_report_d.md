---
title: "Gnome Power Manager, ACPI and my Bios all report different thinngs"
date: 2011-05-17
forum: General Help
---

### Post by Dethdealer on 2011-05-17
Hi,

A couple of days ago I reinstalled Ubuntu 10.10, and I've noticed a rather annoying problem; Gnome's Power Manager is reporting incorrect information.

If I have my laptop on AC power it'll  show 100% straight away with no charging being reported, and if I unplug AC it shoots down to around 82-83%.
GPM is reporting my battery capacity is 83.7% as well, which I'm sure is wrong because both my bios and using "acpi -V" in the terminal both show correct battery information.

I've searched everywhere and I can't  seem to find an answer to this, maybe upgrading to 11.4 would help but I want to stick with 10.10.

My laptop is a Dell Inspiron 1545.

This is my first post, so if I've left anything out tell me xD

---

### Post by Dethdealer on 2011-05-17
Actually, I just checked using "acpi -V" again and it's reporting the design capacity is 2000mAh but the "last full capacity" to be 1673mAh (83%),

The thing is only Ubuntu has reported battery information wrong. Both Windows and my bios report that my battery is perfectly healthy and has near to or actually 100% capacity.

EDIT: Nevermind. No answer, so I just switched back to Windows.

---

