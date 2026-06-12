---
title: "fsck Topics"
date: 2006-03-07
forum: General Help
---

### Post by tritium3 on 2006-03-07
With the 5.10 "Breezy" release, right after installing to an ext3 filesystem, if I reboot into recovery mode and do an fsck on the ext3 partition, I get errors.

Please help if you can.

---

### Post by tritium3 on 2006-03-07
Never mind. My problem was that I needed to boot from the Live CD so that the ext3 partition was not mounted. Then "fsck.ext3 /dev/xxx" showed the filesystem was clean.

---

### Post by dcstar on 2006-03-08
[QUOTE=tritium3]Never mind. My problem was that I needed to boot from the Live CD so that the ext3 partition was not mounted. Then "fsck.ext3 /dev/xxx" showed the filesystem was clean.[/QUOTE]
And you may want to have a quick look at this:

[http://ubuntuforums.org/showthread.php?t=139783](http://ubuntuforums.org/showthread.php?t=139783)

---

