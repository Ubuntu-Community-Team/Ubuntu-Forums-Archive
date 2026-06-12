---
title: "Missing &quot;/dev/disk/by-uuid&quot;"
date: 2012-08-04
forum: General Help
---

### Post by nopcode on 2012-08-04
At some point, a kernel or other update has removed or is no longer creating the /dev/disk/by-uuid folder; only by-id and by-path are in /dev/disk. Missing the uuid causes a problem on boot because fstab is configured to use UUID=mumble for mounting two of the drives. I have to manually hit "S" to force it to continue (nowait doesn't seem to work), and then once booted, can log in as root and sudo mount -a to get them working. This used to work fine for a long time until somewhat recently.

So how do I resolve this, or what has caused this? I'm running kernel 2.6.32-40-server on Ubuntu 10.04.4 LTS (lucid)

---

### Post by nopcode on 2012-08-04
I should have mentioned that the typical answer "change the rootdelay" does not resolve the problem.

---

### Post by PyroSamurai on 2012-10-10
Some system specifications would be nice. What hardware it is on is always relevant.

---

