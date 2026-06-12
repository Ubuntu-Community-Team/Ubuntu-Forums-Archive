---
title: "Don't understand &quot;free memory&quot; display in XFCE"
date: 2009-08-22
forum: General Help
---

### Post by MichiGreat on 2009-08-22
**Hi!**

In XFCE, I have added a small program to my panel that shows me the current disk, mem, and swap usage and the time the system is up. Right now, it shows me a mem usage of 261 MB, but if I enter "cat /proc/meminfo" on the terminal, it shows me the following:

```

MemTotal:      1035364 kB
**MemFree:         31024 kB**
Buffers:         62548 kB
Cached:         673668 kB
SwapCached:          0 kB
Active:         578772 kB
Inactive:       344328 kB
HighTotal:      131008 kB
HighFree:        21684 kB
LowTotal:       904356 kB
LowFree:          9340 kB
SwapTotal:      851436 kB
SwapFree:       851436 kB
Dirty:            1316 kB
Writeback:           0 kB
AnonPages:      186916 kB
Mapped:         331176 kB
Slab:            36396 kB
SReclaimable:    26124 kB
SUnreclaim:      10272 kB
PageTables:       2420 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1369116 kB
Committed_AS:   472516 kB
VmallocTotal:   114680 kB
VmallocUsed:      7964 kB
VmallocChunk:   105972 kB

```

The question now is: How much memory do I have really free? How much memory is used by applications? According to that XFCE panel application, I have "too much" RAM inside my PC (of course I know that one can have never too much RAM inside), according to /proc/meminfo I should put more memory inside.

Is there someone who can make me "unconfused"?

Best regards,

*Michael*

---

### Post by kerry_s on 2009-08-22
use "free -m" in terminal instead.
just don't worry about it, the kernel does a good job with memory.

use the computer, don't worry about the internals.

---

### Post by MichiGreat on 2009-08-22
> **kerry_s said:**
> use "free -m" in terminal instead.
This does yield the same results, just in another way.
> **kerry_s said:**
> just don't worry about it, the kernel does a good job with memory.
It's not about worring, I know that the kernel does a good job.
> **kerry_s said:**
> use the computer, don't worry about the internals
Indeed, I am interested in the internals (I am a software developer). However, I can't agree to your sentence. If my computer has too few RAM, it's *my* job to enhance it. The kernel *can't* do that (yet).

---

### Post by yeeeev on 2009-08-22
When running "free -m" you can see an amount of memory under "cached". This memory is not used by any programs (so it could be described as free), but it is used to cache recently used disk buffers and achieve better performance.
Your "used by programs" memory is actually "used" minus "cached", and your free memory is "free" plus "cached"

---

### Post by MichiGreat on 2010-09-18
> **yeeeev said:**
> When running "free -m" you can see an amount of memory under "cached". This memory is not used by any programs (so it could be described as free), but it is used to cache recently used disk buffers and achieve better performance.
Your "used by programs" memory is actually "used" minus "cached", and your free memory is "free" plus "cached"

Thanks for your reply! Now I understand that. Sorry for answering so late. ;)

---

