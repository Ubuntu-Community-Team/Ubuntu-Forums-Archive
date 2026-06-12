---
title: "init: ureadahead main process (423) terminated with status 5"
date: 2010-12-01
forum: General Help
---

### Post by Skaperen on 2010-12-01
```
init: ureadahead main process (423) terminated with status 5

Ubuntu 10.10 lorentz tty1

lorentz login:
```
The first line of the above shows up during boot before the display goes graphical.  I can see it again (all of the above) when I Ctrl+Alt+F1 to access the first text console.  Anyone know what is causing this, what problems can happen as a result, and what should be done about it?  I moved from 9.10 on one machine to 10.10 on a new machine, so I don't know if it's a hardware problem or software.  I am running 64-bit.  I am not really seeing any problems happening besides the few scattered application and GUI glitches that are common with a new/migrated setup.

---

### Post by dino99 on 2010-12-01
it often happen due to race condition, as its name says, it read ahead the needed packages to boot faster. If it cant for x,y reasons, that error raise, thats it.

This problem is not new and is known, but no need to worry about, this might be fixed soon or later.

---

### Post by Skaperen on 2010-12-01
> **dino99 said:**
> it often happen due to race condition, as its name says, it read ahead the needed packages to boot faster. If it cant for x,y reasons, that error raise, thats it.

This problem is not new and is known, but no need to worry about, this might be fixed soon or later.
If all it is doing is running ahead of things that are going to be read, to read them sooner, then it isn't that big a deal.  I already do something similar to this in my scripts that do some rsync mirroring.  I launch a program that scans the file tree, on the target machine that initiates the rsync, so that all the file metadata is preloaded into RAM, since rsync only accesses that data after the remote source site has collected and delivered it.  It helps parallel things better.  Thanks.

---

