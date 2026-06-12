---
title: "multiple console-kit processes"
date: 2010-07-24
forum: General Help
---

### Post by jynyl on 2010-07-24
In htop, I can see about 50 processes, each named
```
/usr/sbin/console-kit-daemon --no-daemon
```
and apparently each one is using 117MB of memory.

Is this normal?  What do all these processes do?

Running Kubuntu 10.04, 64 bit, on quad core 4GB ram.

*Update:* Over at the [Arch Linux forum]("https://bbs.archlinux.org/viewtopic.php?id=57491"), a post says these are threads of a process, not separate processes.  So maybe this is not such an issue.

---

