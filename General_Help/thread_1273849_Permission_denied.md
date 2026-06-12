---
title: "Permission denied?"
date: 2009-09-23
forum: General Help
---

### Post by sideaway on 2009-09-23
Hey guys, quick q...

wtf?

hamish@hamish-desktop:/$ sudo >update-rc.d PS3MediaServerd defaults 60
bash: update-rc.d: Permission denied

Permission denied from a sudo command?

---

### Post by 3rdalbum on 2009-09-23
What exactly are you trying to do?

The "greater-than" symbol (>) is splitting the command; remove it.

---

### Post by sideaway on 2009-09-23
Haha cheers! Setting a program up to run as a daemon.

---

