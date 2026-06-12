---
title: "problems with 10.04 and older binutils"
date: 2010-05-25
forum: General Help
---

### Post by rgetz on 2010-05-25
Hi.

I'm using 10.04 on a Intel(R) Core(TM)2 Duo CPU T9900  @ 3.06GHz (64-bit OS installed), and I'm running into problems when I build binutils 2.17 from source.

If I move the the source to a 64-bit 9.10 machine, compile things, and move the resulting binary back over to 10.04 - things work fine.

The error that I'm getting is:
./bin/ld: final link failed: File truncated
collect2: ld returned 1 exit status

I'm stumped - other than poking in the ./configure script, and seeing what the difference between the two different config.log files are - I'm not sure.

Any suggestions to help track things down? (a lib to swap maybe?)

Thanks

---

