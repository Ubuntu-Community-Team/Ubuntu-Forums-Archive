---
title: "Memory segment error."
date: 2012-01-17
forum: General Help
---

### Post by colobix on 2012-01-17
Hey guys. I'm getting this error on some games I try to run.
I bought this game "Helena the 3rd" from the ubuntu software center the other day.
But I can't run it. And when I try to run it from the termianl, it says Memory segment error.

What is this? And more importantly, how do I fix it.

---

### Post by BC59 on 2012-01-17
In any case you could run a memory check from the boot screen.

---

### Post by dino99 on 2012-01-17
have you memory errors with some other apps ? First i think to ram stick(s), maybe a memtest can confirm the problem.
If you only have memory issue with this game, then test it with valgrind
if your system have graphic driver issue (check with: sudo jockey-gtk) or temperature issue ( check fans) or the system been overclocked, then probability to get trouble is higher.

---

### Post by colobix on 2012-01-17
Thanks. Jockey only gave me the one driver that is active (NVidia Accelerated graphic driver). It also says it's the recommended driver.

Valgrind gave me this info when I tested the game:

> ==30705== Memcheck, a memory error detector
==30705== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==30705== Using Valgrind-3.6.1 and LibVEX; rerun with -h for copyright info
==30705== Command: /opt/helena-the-3rd/helena-the-3rd
==30705== 
==30705== Conditional jump or move depends on uninitialised value(s)
==30705==    at 0x97EC0CB: __GI___strcasecmp_l (strcmp.S:243)
==30705==    by 0x9785F60: __gconv_open (gconv_open.c:70)
==30705==    by 0x9794106: _nl_find_msg (dcigettext.c:990)
==30705==    by 0x9794818: __dcigettext (dcigettext.c:654)
==30705==    by 0x5D726FE: gtk_get_option_group (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x5D72909: gtk_parse_args (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x5D72978: gtk_init_check (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x494F29: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFBE2: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFE09: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFE54: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x429C28: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705== 
==30705== Use of uninitialised value of size 8
==30705==    at 0x97EE204: __GI___strcasecmp_l (strcmp.S:2257)
==30705==    by 0x9785F60: __gconv_open (gconv_open.c:70)
==30705==    by 0x9794106: _nl_find_msg (dcigettext.c:990)
==30705==    by 0x9794818: __dcigettext (dcigettext.c:654)
==30705==    by 0x5D726FE: gtk_get_option_group (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x5D72909: gtk_parse_args (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x5D72978: gtk_init_check (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x494F29: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFBE2: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFE09: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFE54: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x429C28: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705== 
==30705== Use of uninitialised value of size 8
==30705==    at 0x97EE208: __GI___strcasecmp_l (strcmp.S:2258)
==30705==    by 0x9785F60: __gconv_open (gconv_open.c:70)
==30705==    by 0x9794106: _nl_find_msg (dcigettext.c:990)
==30705==    by 0x9794818: __dcigettext (dcigettext.c:654)
==30705==    by 0x5D726FE: gtk_get_option_group (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x5D72909: gtk_parse_args (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x5D72978: gtk_init_check (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==    by 0x494F29: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFBE2: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFE09: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5BFE54: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x429C28: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705== 
==30705== Invalid read of size 8
==30705==    at 0x42C373: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x42E318: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FC155: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD2A3: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD396: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x538E18: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x4A979A: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x7E8A4EA: ??? (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x7E88BCC: g_main_context_dispatch (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x7E893A7: ??? (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x7E899F1: g_main_loop_run (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x5CF9A2A: gtk_dialog_run (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==30705== 
==30705== 
==30705== Process terminating with default action of signal 11 (SIGSEGV)
==30705==  Access not within mapped region at address 0x0
==30705==    at 0x42C373: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x42E318: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FC155: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD2A3: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD396: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x538E18: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x4A979A: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x7E8A4EA: ??? (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x7E88BCC: g_main_context_dispatch (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x7E893A7: ??? (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x7E899F1: g_main_loop_run (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==    by 0x5CF9A2A: gtk_dialog_run (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==30705==  If you believe this happened as a result of a stack
==30705==  overflow in your program's main thread (unlikely but
==30705==  possible), you can try to increase the size of the
==30705==  main thread stack using the --main-stacksize= flag.
==30705==  The main thread stack size used in this run was 8388608.
==30705== Invalid read of size 8
==30705==    at 0x98A1865: free_derivation (in /lib/x86_64-linux-gnu/libc-2.13.so)
==30705==    by 0x98492DC: tdestroy (tsearch.c:643)
==30705==    by 0x98A2991: __libc_freeres (in /lib/x86_64-linux-gnu/libc-2.13.so)
==30705==    by 0x4A235A8: _vgnU_freeres (vg_preloaded.c:62)
==30705==    by 0x179FB81F: ???
==30705==    by 0x42E318: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FC155: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD2A3: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD396: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x538E18: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x4A979A: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x7E8A4EA: ??? (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==  Address 0x18 is not stack'd, malloc'd or (recently) free'd
==30705== 
==30705== 
==30705== Process terminating with default action of signal 11 (SIGSEGV)
==30705==  Access not within mapped region at address 0x18
==30705==    at 0x98A1865: free_derivation (in /lib/x86_64-linux-gnu/libc-2.13.so)
==30705==    by 0x98492DC: tdestroy (tsearch.c:643)
==30705==    by 0x98A2991: __libc_freeres (in /lib/x86_64-linux-gnu/libc-2.13.so)
==30705==    by 0x4A235A8: _vgnU_freeres (vg_preloaded.c:62)
==30705==    by 0x179FB81F: ???
==30705==    by 0x42E318: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FC155: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD2A3: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x5FD396: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x538E18: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x4A979A: ??? (in /opt/helena-the-3rd/helena-the-3rd)
==30705==    by 0x7E8A4EA: ??? (in /lib/x86_64-linux-gnu/libglib-2.0.so.0.2800.6)
==30705==  If you believe this happened as a result of a stack
==30705==  overflow in your program's main thread (unlikely but
==30705==  possible), you can try to increase the size of the
==30705==  main thread stack using the --main-stacksize= flag.
==30705==  The main thread stack size used in this run was 8388608.
==30705== 
==30705== HEAP SUMMARY:
==30705==     in use at exit: 5,414,481 bytes in 24,608 blocks
==30705==   total heap usage: 96,480 allocs, 71,872 frees, 18,119,179 bytes allocated
==30705== 
==30705== LEAK SUMMARY:
==30705==    definitely lost: 2,764 bytes in 11 blocks
==30705==    indirectly lost: 6,649 bytes in 196 blocks
==30705==      possibly lost: 1,354,555 bytes in 11,570 blocks
==30705==    still reachable: 4,050,513 bytes in 12,831 blocks
==30705==         suppressed: 0 bytes in 0 blocks
==30705== Rerun with --leak-check=full to see details of leaked memory
==30705== 
==30705== For counts of detected and suppressed errors, rerun with: -v
==30705== Use --track-origins=yes to see where uninitialised values come from
==30705== ERROR SUMMARY: 20 errors from 5 contexts (suppressed: 10 from 8)


Any idea what the problem could be?

---

### Post by colobix on 2012-01-19
Bump

---

### Post by colobix on 2012-01-21
Bump!

Please help

---

### Post by colobix on 2012-01-22
Bump

---

### Post by colobix on 2012-01-23
**BUMP**
Please help.

---

### Post by pbrane on 2012-01-23
> **colobix said:**
> **BUMP**
Please help.

Try running the game from a terminal and post any error message you see. Sometimes running in a terminal will clarify things.

This may help. It may even be you!
[http://helenathe3rd.proboards.com/index.cgi?board=bugs&action=display&thread=26]("http://helenathe3rd.proboards.com/index.cgi?board=bugs&action=display&thread=26")

---

### Post by colobix on 2012-01-23
> **pbrane said:**
> Try running the game from a terminal and post any error message you see. Sometimes running in a terminal will clarify things.

This may help. It may even be you!
[http://helenathe3rd.proboards.com/index.cgi?board=bugs&action=display&thread=26]("http://helenathe3rd.proboards.com/index.cgi?board=bugs&action=display&thread=26")
Thanks but no help there.
Also0 I use 11.04, so it may be a different problem.

I have already ran the game from terminal, as I said in my first post. Nothing more than that memory error.

---

### Post by colobix on 2012-01-24
Bump

---

### Post by colobix on 2012-01-25
**BUMP**
Any help here please?

---

### Post by colobix on 2012-01-27
**[color="magenta"][size="10"]bump[/size][/color]**

---

