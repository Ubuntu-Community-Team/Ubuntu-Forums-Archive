---
title: "Transmission error"
date: 2010-04-26
forum: General Help
---

### Post by Geiste on 2010-04-26
I everyone

I'm getting this error:

Transmission cannot be started
Couldn't open "/home/user/.config/transmission/lock": Input/output error

This happened after a system crash and reboot. 

I'm new in linux, so i will appreciate if you tell me how to solve this problem step by step.

Thanks

---

### Post by KayakJim on 2010-04-26
> **Geiste said:**
> I everyone

I'm getting this error:

Transmission cannot be started
Couldn't open "/home/user/.config/transmission/lock": Input/output error

This happened after a system crash and reboot. 

I'm new in linux, so i will appreciate if you tell me how to solve this problem step by step.

Thanks

Have you tried deleting the file specified? Since your system crashed, the file may have been left open, which is why it cannot be opened.

---

### Post by Yellow Pasque on 2010-04-26
If Transmission was running during the crash, it may have left a stale lock file.
```
rm ~/.config/transmission/lock
```

---

### Post by Geiste on 2010-04-26
[LEFT]KayakJim and Temujin, thanks.

Problem solved
[/LEFT]

---

