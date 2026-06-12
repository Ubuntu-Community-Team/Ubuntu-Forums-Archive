---
title: "Evolution 2.28.2 Segmentation Fault (Ubuntu 10.04.3)"
date: 2011-12-30
forum: General Help
---

### Post by Chrison999 on 2011-12-30
Hi folks!

When I run Evolution, it loads just fine.  However, when I go to send a new e-mail or reply to an existing e-mail, Evolution crashes.  Running it with "--debug=filename" doesn't give any information, but running it with "gdb evolution" and then "start" produces this output:

Program received signal SIGSEGV, Segmentation fault.
0x00007fffebedf788 in ?? () from /lib/libc.so.6

I have tried un-installing and re-installing Evolution, but get the same thing.  Any help or suggestions would be greatly appreciated!

Thanks!

Regards,

Chris

---

