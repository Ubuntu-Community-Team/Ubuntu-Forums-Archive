---
title: "mplayer not working"
date: 2004-10-21
forum: General Help
---

### Post by Vulc on 2004-10-21
this is the error I get when I run gmplayer, I installed removed, installed again, no dice =(

MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon 4 /Athlon MP/XP Palomino 1855 MHz (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Reading config file /etc/mplayer/mplayer.conf
Illegal instruction

and it dies right there

---

### Post by K6-III on 2004-10-21
For one, it looks like it was compiled for SSE2 chips, not like yours, which is only SSE.

---

