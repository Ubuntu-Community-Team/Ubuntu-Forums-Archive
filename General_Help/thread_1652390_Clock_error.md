---
title: "Clock error"
date: 2010-12-24
forum: General Help
---

### Post by khha4113 on 2010-12-24
It has been since I installed Ubuntu from earlier version to 10.10.  My computer is dual-boot between Windows 7 and Ubuntu, and any time I log out of Ubuntu and boot into Windows somehow Ubuntu has changed my clock in BIOS back to 8 hours.  I have to manually either reset it back to my area's time (Pacific Time) in BIOS or in Windows 7.  It's not the problem but more like annoyance.  Anyone knows how to fix this?  Thanks.

---

### Post by noah++ on 2010-12-24
You need to configure Ubuntu to use a local time hardware clock or configure Windows to use a UTC hardware clock.

---

### Post by khha4113 on 2010-12-24
> **noah++ said:**
> You need to configure Ubuntu to use a local time hardware clock or configure Windows to use a UTC hardware clock.

Thanks for your help.  I found the way by editing rcS to set UTC=no so Ubuntu know the hardware clock is running in local time.

---

### Post by cactusns on 2011-05-24
I am a new ubuntu user. I don't know how to configure Ubuntu to use a local time hardware clock or configure Windows to use a UTC hardware clock. Can you show it more details?

---

