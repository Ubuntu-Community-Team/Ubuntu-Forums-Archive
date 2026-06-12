---
title: "Disk Check problem"
date: 2010-06-19
forum: General Help
---

### Post by jdunn on 2010-06-19
During disk checks (forced or otherwise)on boot for my laptop, the test gets to about 96% before the test-progress vanishes and then appears to hang, showing nothing but the chevron.  I have to ctrl-alt-del to reboot.  Is there a quick, easy way to perform the disk check in text mode so I can better understand what's going on?  Also, which log-file can help me diagnose the problem?

---

### Post by TeoBigusGeekus on 2010-06-19
Boot up with a live cd and fsck the disks.

---

### Post by jdunn on 2010-06-19
> **TeoBigusGeekus said:**
> Boot up with a live cd and fsck the disks.

Did what you suggested but it was really fast and I don't think it did a thorough check.

fsck /dev/sda5
It said the partition was clean.

---

### Post by philinux on 2010-06-19
> **jdunn said:**
> Did what you suggested but it was really fast and I don't think it did a thorough check.

fsck /dev/sda5
It said the partition was clean.

Try booting into recovery mode. Then resume normal boot. Then reboot normally.
p.s. I moved your post out of the sticky as no solution was given.
Stick is for "issues/bugs with workarounds".

---

