---
title: "Wierd Ram Upgrade Issue"
date: 2009-07-02
forum: General Help
---

### Post by MasterMaxus on 2009-07-02
Hi People

I'm running hardy heron, current running with 2GB of ram in two single sticks, Im upgrading to 8GB (4 x 2GB) and the machine hangs at the please wating load .... on boot, the symptoms are exactly the same as this issue:

Fix 'ALERT! : dev/XYZ does not exist' -> [http://ubuntuforums.org/showthread.php?t=197956](http://ubuntuforums.org/showthread.php?t=197956)

Except I haven't changed any of the harddrives in my machine, just the ram, its as if the loader, has reassigned the drive due to the extra ram.

Any ideas to whats happening and how to fix it? 

uname -a = Linux TeraServer 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux

Thanks People!
-Maxus

---

### Post by theozzlives on 2009-07-02
What's your specs of the machine?

---

### Post by MasterMaxus on 2009-07-02
Hi theozzlives,

Thanks for your reply,

the machine is a:
AMD Athlon64 AM2 4200+
Gigabyte GA-MA790fx-DQ6
Highpoint 1640 raid card.

The machine has 8 hard drives, 4 500GB (office file shares) 3 300GB (office backups) and 1 200GB drive for OS, all are connected via SATA the os dirve is connected to the MOBO on board sata.
and just a cheap graphics card. This is the office file server. 

I would post the exact error but i cant find where it is being logged to. Any idea where is would be logged?

This has me rather stumpped, if i put the old ram back in the machine boots fine.

Thanks!
Maxus

---

### Post by charonred on 2009-11-01
Try upgrading the BIOS to latest version

---

