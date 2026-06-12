---
title: "read only?"
date: 2010-06-26
forum: General Help
---

### Post by UncleMonty on 2010-06-26
For some reason my entire system is now set as read only. Any advice is welcomed, all questions will be answered.

---

### Post by yetiman64 on 2010-06-26
What version are you running?

It sounds like your OS has been remounted as read only because of a filesystem error.

for eg. from my /etc/fstab> # Entry for /dev/sda6 :
UUID=5e22d316-8ebb-4ae3-a694-a0d6bd2751f5 / ext4 **errors=remount-ro** 0 1
to see your fstab do in a terminal

```
cat /etc/fstab
```To fix will need "fsck" run on the / partition and may need to be done from a live cd as you shouldn't do a filesystem check on a mounted partition. Let us know your situation. 

You can force a complete filesystem check by putting a blank file called "forcefsck" in the root partition and reboot (writing it may need to be done from a live cd if the filesystem is read-only)

Note: you can access this forum from the live cd if needed.

---

### Post by diesch on 2010-06-26
Most likely there is a file system error. Linux sets file systems to read-only when it find an error to prevent further damage.

Run
```
 sudo touch /forcefsck
```
from the command line and reboot. That forces the system to run a file system check on startup.

---

### Post by UncleMonty on 2010-06-26
> **diesch said:**
> Most likely there is a file system error. Linux sets file systems to read-only when it find an error to prevent further damage.

Run
```
 sudo touch /forcefsck
```
from the command line and reboot. That forces the system to run a file system check on startup.

Sorted thanks!

---

