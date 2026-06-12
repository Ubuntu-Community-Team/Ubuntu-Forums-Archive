---
title: "Compaq sr1033wm Power off module"
date: 2011-01-07
forum: General Help
---

### Post by simonthecat on 2011-01-07
I have a Compaq Preesaria sr1033wm. Currently I am running Ubuntu 11.04, but this problem seems to affect all version of Ubuntu I have tried.

When I shutdown my computer the system will not automatically poweroff. It takes it to the system halted then I have to push the power button.

I used to run straight Debian on this machine and to fix this I did this:
```
modprobe apm power_off=1

```

In Ubuntu when I run that command I get:
```
FATAL: Error inserting apm (/lib/modules/2.6.35-22-generic/kernel/arch/x86/kernel/apm.ko): No such device

```

There must be a module somewhere that would make this work, but I have not been able to figure it out. Thank you for your help.

---

