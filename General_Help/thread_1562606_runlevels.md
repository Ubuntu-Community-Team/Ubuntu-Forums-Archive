---
title: "runlevels"
date: 2010-08-27
forum: General Help
---

### Post by safee1248 on 2010-08-27
Changing runlevels is there a different way of doing it?

---

### Post by AlphaLexman on 2010-08-27
Do you mean besides:
```
sudo init 5
```

---

### Post by safee1248 on 2010-08-27
yes

---

### Post by AlphaLexman on 2010-08-27
> **init** is the first process run by any Unix machine at boot time. It verifies the integrity of all filesystems and then creates other processes, using **fork** and **exec**, as specified by */etc/inittab*. Which processes may be run is controlled by *runlevel*. All process terminations are recorded in */var/run/utmp* and */var/log/wtmp*. When the runlevel changes, **init** sends SIGTERM and then, after 20 seconds, SIGKILL to all processes that cannot be run in the new runlevel.from Linux in a Nutshell.

---

