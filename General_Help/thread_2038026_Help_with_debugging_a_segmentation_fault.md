---
title: "Help with debugging a segmentation fault"
date: 2012-08-05
forum: General Help
---

### Post by manjaba on 2012-08-05
I got the following when I ran gdb on a program, SimpleDemo, which indicated a segmentation fault:


(gdb) run
Starting program: /home/bill/asm/SimpleDemo 

Program received signal SIGSEGV, Segmentation fault.
0xb7e56590 in ?? () from /lib/i386-linux-gnu/libc.so.6

I was expecting to get info on where the program created the fault but it seems it was caused in one of the c libraries. Not sure where to go with this as I was following along with a debug tutorial and am now in (for me) uncharted waters.

Thanks,

Bill

---

