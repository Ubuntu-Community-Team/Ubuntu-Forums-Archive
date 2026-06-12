---
title: "K(Copy Crashing in Ubuntu 11.04 when trying to open a DVD"
date: 2011-06-25
forum: General Help
---

### Post by lefo on 2011-06-25
I get the following from the crash report:

Application: k9copy (k9copy), signal: Segmentation fault
[Current thread is 1 (Thread 0xb7866710 (LWP 2652))]

Thread 4 (Thread 0xb7609b70 (LWP 2654)):
#0  0x0037f371 in pthread_mutex_lock () from /lib/i386-linux-gnu/libpthread.so.0
#1  0x02289752 in g_main_context_check () from /lib/i386-linux-gnu/libglib-2.0.so.0
#2  0x0228a03a in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x0228a92b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x02174304 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#5  0x022b32df in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#6  0x0037ce99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#7  0x01cdf73e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 3 (Thread 0xb6e08b70 (LWP 2655)):
#0  0x00394416 in __kernel_vsyscall ()
#1  0x01ced753 in ?? () from /lib/i386-linux-gnu/libc.so.6
#2  0x01c80b94 in ?? () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: previous frame identical to this frame (corrupt stack?)

Thread 2 (Thread 0xb4724b70 (LWP 2656)):
#0  0x00394416 in __kernel_vsyscall ()
#1  0x01ced753 in ?? () from /lib/i386-linux-gnu/libc.so.6
#2  0x01c80b94 in ?? () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: previous frame identical to this frame (corrupt stack?)

Thread 1 (Thread 0xb7866710 (LWP 2652)):
[KCrash Handler]
#7  0x01c7c9f1 in ?? () from /lib/i386-linux-gnu/libc.so.6
#8  0x01c7ef53 in malloc () from /lib/i386-linux-gnu/libc.so.6
#9  0x0811497f in ___DVDReadBytes ()
#10 0x0811cabc in ___ifoRead_PGCI_UT ()
#11 0x0811fdd6 in ?? ()
#12 0x0811fffd in ___ifoOpen ()
#13 0x080fc4f5 in ?? ()
#14 0x080f5695 in ?? ()
#15 0x080ebe0b in ?? ()
#16 0x0809c088 in ?? ()
#17 0x08066b53 in _start ()

I've gone through all of the suggested dependencies, and they seem to be there, but I honestly don't know how to read the above to know if/what's going on.

Help?!?!?

Thanks. :D

---

