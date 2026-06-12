---
title: "dvipdf/dvips not working after upgrade to 10.04"
date: 2011-06-02
forum: General Help
---

### Post by mayor defacto on 2011-06-02
Hello all,

This is my first post here, so sorry if I have missed an existing thread on this topic (there were a couple, but it didn't seem like the problem was resolved).

I upgraded Ubuntu 9.X to 10.04 a couple of months ago, and since then I have been having problems using dvipdf an dvips to convert Latex generated dvi files.

The error I get concerns an invalid pointer of some description:

*** glibc detected *** dvips: free(): invalid pointer: 0x000000000263a241 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f36e5b425b6]
/usr/lib/libkpathsea.so.4(+0x8b7d)[0x7f36e60d9b7d]
/usr/lib/libkpathsea.so.4(kpse_fontmap_lookup+0xd9)[0x7f36e60d9df9]
/usr/lib/libkpathsea.so.4(kpse_find_file+0x3e0)[0x7f36e60d6690]
dvips[0x413e63]
.
.
*** LOTS OF SIMILAR STUFF ***
.
.
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f36e5ae9c4d]
dvips[0x402369]
======= Memory map: ========
00400000-00431000 r-xp 00000000 08:01 7696                               /usr/bin/dvips
00630000-00631000 r--p 00030000 08:01 7696                               /usr/bin/dvips
00631000-00632000 rw-p 00031000 08:01 7696                               /usr/bin/dvips
00632000-00650000 rw-p 00000000 00:00 0 
02438000-0264e000 rw-p 00000000 00:00 0                                  [heap]
.
.
*** LOTS OF SIMILAR STUFF ***
.
.
Aborted (core dumped)


Does anyone know where the problem may lie? I don't know much about this stuff, but thought Ghostscript might responsible, but after reinstalling I still get the same problem.

Thanks in advance for helping.

Cheers, MdF

---

### Post by mayor defacto on 2011-06-06
I left it a few days, but no nibbles.

One last cry for help! Anyone got any ideas before the thread sinks into the abyss?

Thanks again, MdF

---

