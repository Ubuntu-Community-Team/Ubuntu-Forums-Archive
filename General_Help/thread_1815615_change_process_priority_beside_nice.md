---
title: "change process priority beside nice"
date: 2011-07-31
forum: General Help
---

### Post by FV4bX on 2011-07-31
Hi all,

when i read about the nice command, i saw that the nice value is actually just a hint to the scheduler that may be ignored:
```
info coreutils 'nice invocation'
```
> A niceness should not be confused with a scheduling priority, which
lets applications determine the order in which threads are scheduled to
run.  Unlike a priority, a niceness is merely advice to the scheduler,
which the scheduler is free to ignore.

Is there any way to set a processes priority so that the scheduler would _definitely_ favor that process?

Thanks in advance
FV4bX

---

