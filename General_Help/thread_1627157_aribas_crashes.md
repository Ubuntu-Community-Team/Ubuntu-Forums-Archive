---
title: "aribas crashes"
date: 2010-11-21
forum: General Help
---

### Post by Gommer on 2010-11-21
I'm using ubuntu 10.10 386 32 bit version.
With Ubuntu Software Center I installed the package aribas.
When I try to load a file it crashes:

d@ubuntu:~/aribas$ aribas

ARIBAS Interpreter for Arithmetic, V 1.64a, Feb. 2010 (LINUX386)
Copyright (C) 1996-2010 O.Forster <forster@mathematik.uni-muenchen.de>

ARIBAS comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under the terms of the GNU
General Public License as published by the Free Software Foundation.


for help, type  ?
to return from ARIBAS, type  exit

==> load ("fac").
*** glibc detected *** aribas: free(): invalid next size (normal): 0x099fa690 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0xb7613501]
/lib/libc.so.6(+0x6dd70)[0xb7614d70]
/lib/libc.so.6(cfree+0x6d)[0xb7617e5d]
/lib/libc.so.6(fclose+0x14a)[0xb760381a]
aribas[0x8066481]
aribas[0x806653b]
aribas[0x806735f]
aribas[0x8065ab3]
aribas[0x80685cd]
aribas[0x806869e]
/lib/libc.so.6(__libc_start_main+0xe7)[0xb75bdce7]
aribas[0x8048bf1]
======= Memory map: ========
08048000-08076000 r-xp 00000000 07:00 1188691    /usr/bin/aribas
08076000-08077000 r-xp 0002d000 07:00 1188691    /usr/bin/aribas
08077000-08078000 rwxp 0002e000 07:00 1188691    /usr/bin/aribas
08078000-0807a000 rwxp 00000000 00:00 0 
099c3000-09a0b000 rwxp 00000000 00:00 0          [heap]
b6c00000-b6c21000 rwxp 00000000 00:00 0 
b6c21000-b6d00000 ---p 00000000 00:00 0 
b6d43000-b6d5d000 r-xp 00000000 07:00 392528     /lib/libgcc_s.so.1
b6d5d000-b6d5e000 r-xp 00019000 07:00 392528     /lib/libgcc_s.so.1
b6d5e000-b6d5f000 rwxp 0001a000 07:00 392528     /lib/libgcc_s.so.1
b6d6d000-b75a7000 rwxp 00000000 00:00 0 
b75a7000-b76fe000 r-xp 00000000 07:00 392543     /lib/libc-2.12.1.so
b76fe000-b76ff000 ---p 00157000 07:00 392543     /lib/libc-2.12.1.so
b76ff000-b7701000 r-xp 00157000 07:00 392543     /lib/libc-2.12.1.so
b7701000-b7702000 rwxp 00159000 07:00 392543     /lib/libc-2.12.1.so
b7702000-b7705000 rwxp 00000000 00:00 0 
b7711000-b7715000 rwxp 00000000 00:00 0 
b7715000-b7716000 r-xp 00000000 00:00 0          [vdso]
b7716000-b7732000 r-xp 00000000 07:00 392508     /lib/ld-2.12.1.so
b7732000-b7733000 r-xp 0001b000 07:00 392508     /lib/ld-2.12.1.so
b7733000-b7734000 rwxp 0001c000 07:00 392508     /lib/ld-2.12.1.so
bfb0e000-bfb2f000 rwxp 00000000 00:00 0          [stack]
Aborted
:sad:
The file fac.ari exists in the directory where I start aribas.


Note: It also crashes if you just start aribas, and the you type 
exit. <CR>

---

