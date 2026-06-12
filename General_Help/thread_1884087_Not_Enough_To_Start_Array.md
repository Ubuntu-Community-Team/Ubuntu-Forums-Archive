---
title: "Not Enough To Start Array"
date: 2011-11-20
forum: General Help
---

### Post by naicidrac on 2011-11-20
I have 5 X 2TB drives in a RAID 5 config and I was running 11.04.  I reinstalled 11.10 on my OS drive and now I see all of the 2TB drives and they say they are part of a RAID Aray, but are unable to start because "Not running, Not enought components to start RAID array".

Thanks for the help,
Naicidrac

---

### Post by naicidrac on 2011-11-20
Resolved!

Just realized I needed to install mdamd and xfs progs.  After a reboot I was good and mounted RAID.

---

### Post by philinux on 2011-11-20
> **naicidrac said:**
> Resolved!

Just realized I needed to install mdamd and xfs progs.  After a reboot I was good and mounted RAID.

Well done. I looked at your post earlier and did not have a clue. Never used raid. I guess those apps are not part of the default install.

---

