---
title: "compiz crash lately"
date: 2009-11-09
forum: General Help
---

### Post by Olivier Lec on 2009-11-09
since I have upgraded to 9.10, my compiz is really instable 

I have some crash every 4~5 hours with following log 
```

gdb) (gdb)
Thread 1 (Thread 0x7f7d1dd64780 (LWP 9950)):
#0  0x00007f7d1bb60a8e in waitpid () from /lib/libc.so.6
#1  0x00007f7d1bafe1f9 in ?? () from /lib/libc.so.6
#2  0x00007f7d0ffe18a7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  <signal handler called>
#4  0x00007f7d0a0584a8 in ?? () from /usr/lib/compiz/libwobbly.so
#5  0x00007f7d09c3393d in ?? () from /usr/lib/compiz/libexpo.so
#6  0x00007f7d09a29ea6 in ?? () from /usr/lib/compiz/libezoom.so
#7  0x00007f7d09820599 in ?? () from /usr/lib/compiz/libfade.so
#8  0x00007f7d0961ab6a in ?? () from /usr/lib/compiz/libswitcher.so
#9  0x00007f7d0940fab0 in ?? () from /usr/lib/compiz/libscale.so
#10 0x0000000000412d27 in eventLoop ()
#11 0x000000000040d650 in main ()
(gdb)
(gdb)
(gdb) #0  0x00007f7d1bb60a8e in waitpid () from /lib/libc.so.6
#1  0x00007f7d1bafe1f9 in ?? () from /lib/libc.so.6
#2  0x00007f7d0ffe18a7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  <signal handler called>
#4  0x00007f7d0a0584a8 in ?? () from /usr/lib/compiz/libwobbly.so
#5  0x00007f7d09c3393d in ?? () from /usr/lib/compiz/libexpo.so
#6  0x00007f7d09a29ea6 in ?? () from /usr/lib/compiz/libezoom.so
#7  0x00007f7d09820599 in ?? () from /usr/lib/compiz/libfade.so
#8  0x00007f7d0961ab6a in ?? () from /usr/lib/compiz/libswitcher.so
#9  0x00007f7d0940fab0 in ?? () from /usr/lib/compiz/libscale.so
#10 0x0000000000412d27 in eventLoop ()
#11 0x000000000040d650 in main ()
(gdb) A debugging session is active.

```
Any suggestions ?

---

