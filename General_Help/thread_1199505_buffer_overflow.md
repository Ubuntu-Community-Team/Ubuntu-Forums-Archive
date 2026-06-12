---
title: "*******buffer overflow****************"
date: 2009-06-29
forum: General Help
---

### Post by mamali on 2009-06-29
i have build a program but when i make it and run it suddenly it kills
heeeeeeeeeeeeeeeeelp pleaaaaaaase
and this is the error:
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d81558]
/lib/tls/i686/cmov/libc.so.6[0xb7d7f680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7d7e944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c9d685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
08b80000-08ba1000 rw-p 08b80000 00:00 0          [heap]
b7479000-b747a000 ---p b7479000 00:00 0 
b747a000-b7c7a000 rw-p b747a000 00:00 0 
b7c7a000-b7c84000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c84000-b7c85000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c85000-b7c86000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c86000-b7c87000 rw-p b7c86000 00:00 0 
b7c87000-b7ddf000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7ddf000-b7de1000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7de1000-b7de2000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7de2000-b7de5000 rw-p b7de2000 00:00 0 
b7de5000-b7df2000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7df2000-b7df3000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7df3000-b7df4000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7df4000-b7e18000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e18000-b7e19000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e19000-b7e1a000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e1a000-b7e1b000 rw-p b7e1a000 00:00 0 
b7e1b000-b7efe000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7efe000-b7eff000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7eff000-b7f03000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f03000-b7f04000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f04000-b7f0a000 rw-p b7f04000 00:00 0 
b7f0a000-b7f1f000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f1f000-b7f20000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f20000-b7f21000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f21000-b7f23000 rw-p b7f21000 00:00 0 
b7f37000-b7f3a000 rw-p b7f37000 00:00 0 
b7f3a000-b7f54000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b7f54000-b7f55000 r-xp b7f54000 00:00 0          [vdso]
b7f55000-b7f56000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b7f56000-b7f57000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bf841000-bf856000 rw-p bffeb000 00:00 0          [stack]

---

### Post by t4thfavor on 2009-06-29
Its putting a string of x+1 characters into a box designed to hold only x chars. Contact the developers as this could be concidered a security flaw.

That said there is probaby some way to get your compiler to ignore this error (semi safely) and allow the program to continue.

---

