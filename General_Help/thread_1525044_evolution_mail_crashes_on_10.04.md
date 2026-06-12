---
title: "evolution mail crashes on 10.04"
date: 2010-07-06
forum: General Help
---

### Post by kahnoie on 2010-07-06
Evolution reports a segmentation fault and crashes:
[  427.787672] evolution[2914]: segfault at 4 ip 06bd23b9 sp b2b6e1f0 error 4 in libglib-2.0.so.0.2400.1[6b78000+c8000]

I am currently using 2.6.32-22-generic #36-Ubuntu

The last part of the O/P from gdb evolution --ex r --ex "t a a bt" --ex q
[New Thread 0xadaafb70 (LWP 16877)]
[New Thread 0xad1c2b70 (LWP 16878)]
[New Thread 0xac5ffb70 (LWP 16879)]
[New Thread 0xabdfeb70 (LWP 16880)]
[Thread 0xaf9f3b70 (LWP 16875) exited]
[Thread 0xabdfeb70 (LWP 16880) exited]
[Thread 0xad1c2b70 (LWP 16878) exited]
[Thread 0xac5ffb70 (LWP 16879) exited]
[Thread 0xb13f7b70 (LWP 16873) exited]
[Thread 0xb45ffb70 (LWP 16874) exited]
[Thread 0xb56ffb70 (LWP 16872) exited]
[Thread 0xb3dfeb70 (LWP 16876) exited]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xadaafb70 (LWP 16877)]
0x0165e3b9 in ?? () from /lib/libglib-2.0.so.0

Thread 1551 (Thread 0xadaafb70 (LWP 16877)):
#0  0x0165e3b9 in ?? () from /lib/libglib-2.0.so.0
#1  0x0165e7b4 in ?? () from /lib/libglib-2.0.so.0
#2  0x008603ef in __nptl_deallocate_tsd () from /lib/tls/i686/cmov/libpthread.so.0
#3  0x0086097c in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x0179ba4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 202 (Thread 0xb6657b70 (LWP 13552)):
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x0178db86 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x016504eb in g_poll () from /lib/libglib-2.0.so.0
#3  0x016430ac in ?? () from /lib/libglib-2.0.so.0
#4  0x01643817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x00c5f400 in ?? () from /usr/lib/libORBit-2.so.0
#6  0x01669def in ?? () from /lib/libglib-2.0.so.0
#7  0x0086096e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x0179ba4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 201 (Thread 0xb29f9b70 (LWP 13551)):
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x0178db86 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x016504eb in g_poll () from /lib/libglib-2.0.so.0
#3  0x016430ac in ?? () from /lib/libglib-2.0.so.0
---Type <return> to continue, or q <return> to quit---return
#4  0x01643817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x00571922 in ?? () from /usr/lib/libebook-1.2.so.9
#6  0x01669def in ?? () from /lib/libglib-2.0.so.0
#7  0x0086096e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x0179ba4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 22 (Thread 0xb31fab70 (LWP 2949)):
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x00865015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x01619b7e in ?? () from /lib/libglib-2.0.so.0
#3  0x01619f7e in g_async_queue_pop () from /lib/libglib-2.0.so.0
#4  0x005ab39d in ?? () from /usr/lib/libcamel-1.2.so.14
#5  0x01669def in ?? () from /lib/libglib-2.0.so.0
#6  0x0086096e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x0179ba4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 21 (Thread 0xb09f5b70 (LWP 2948)):
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x00865015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x01619b7e in ?? () from /lib/libglib-2.0.so.0
#3  0x01619f7e in g_async_queue_pop () from /lib/libglib-2.0.so.0
#4  0x005ab39d in ?? () from /usr/lib/libcamel-1.2.so.14
#5  0x01669def in ?? () from /lib/libglib-2.0.so.0
#6  0x0086096e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x0179ba4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 20 (Thread 0xaf1f2b70 (LWP 2947)):
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x00865015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x01619b7e in ?? () from /lib/libglib-2.0.so.0
#3  0x01619f7e in g_async_queue_pop () from /lib/libglib-2.0.so.0
#4  0x005ab3cf in ?? () from /usr/lib/libcamel-1.2.so.14
#5  0x01669def in ?? () from /lib/libglib-2.0.so.0
#6  0x0086096e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x0179ba4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 18 (Thread 0xb01f4b70 (LWP 2945)):
#0  0x0012d422 in __kernel_vsyscall ()

---

### Post by dino99 on 2010-07-06
subscribe to it

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/576346](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/576346)

try to remove/purge then reinstall libxml2 or

sudp dpkg-reconfigure libxml2

---

