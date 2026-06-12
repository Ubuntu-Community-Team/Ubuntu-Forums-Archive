---
title: "How do make moblock watchdog not check every 5 minutes?"
date: 2010-06-19
forum: General Help
---

### Post by s3a on 2010-06-19
I DO want the watchdog enabled but I want it to run every 60 minutes instead. How do I do that?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by jre on 2010-06-20
Set in /etc/blockcontrol/blockcontrol.conf:
```
WD_SLEEP="3600"
```

You'll find all configuration options documented in /usr/lib/blockcontrol/blockcontrol.defaults

---

