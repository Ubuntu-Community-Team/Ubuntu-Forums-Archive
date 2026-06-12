---
title: "How to change startup script sequence?"
date: 2010-09-18
forum: General Help
---

### Post by Bloodrule on 2010-09-18
I have an external drive mounted courtesy of an entry in fstab.  The drive isn't detected at boot time until AFTER the backuppc service that will use the drive has started.  I have to therefore manually stop and restart the backuppc service once booting has completed, otherwise backuppc thinks there is no drive available to it.

How can I force the mounting of my external device to occur BEFORE the backuppc service starts?

---

### Post by Bloodrule on 2010-09-19
Turns out the reason the external drive wasn't mounted wasn't because fstab chimed in after backuppc, but because fstab had the wrong settings.  Changing noauto to auto solved the problem.  This meant that my external drive was mounted automatically and backuppc found it first time.

Wrong:
/dev/sdb1       /var/lib/backuppc       auto    rw,noauto,user,exec       0       0

Right:
/dev/sdb1       /var/lib/backuppc       auto    rw,auto,user,exec       0       0

---

### Post by weblordpepe on 2010-09-19
yo dude mark it as solved! ya never know who might need this in the future. (and to whoever found this from searching in google years from now - youre welcome)

---

