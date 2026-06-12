---
title: "Nautilus segfault"
date: 2010-04-05
forum: General Help
---

### Post by phen0m on 2010-04-05
It seems to only happen when I'm copying files, and maybe only from ntfs to ext3.  I can't reproduce it reliably.

I lose all desktop icons and all Nautilus windows close.  Copies are aborted.

from dmesg:
```
[  235.146365] nautilus[2879]: segfault at 18 ip 00000000004cc82e sp 00007fff50f0d8f0 error 4 in nautilus[400000+1af000]
```

Does this look like a bug?

---

### Post by NightwishFan on 2010-04-05
Something is obviously happening. If you figure it out more perhaps report a bug by following the guide here:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

