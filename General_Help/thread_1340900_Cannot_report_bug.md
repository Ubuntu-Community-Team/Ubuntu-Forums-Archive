---
title: "Cannot report bug"
date: 2009-11-29
forum: General Help
---

### Post by Poyntz on 2009-11-29
Hi folks,

I've tried selecting several running processes in system monitor, then clicking Help -> Report Bug...

I can't report bugs on any of the running processes. I get the following error message:

[B]The problem cannot be reported:

This is not a genuine Ubuntu package[/B]

I've attempted to report bugs for plasma-desktop, kopete, amarok, okular (just for testing purposes) and obex-data-server and others for true reports.

Nothing has worked.

**Temporary Fix:**
1) In terminal- ```
ps ax|grep (process name)
```
2) Copy and paste the ID for the process
2) Hit Alt+F2
3) ```
ubuntu-bug <pasted process ID>
```

If there's a way to fix the reporting process in System Monitor please specify it.

---

### Post by Poyntz on 2009-12-12
bump

---

