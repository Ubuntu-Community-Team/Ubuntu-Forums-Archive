---
title: "c++ program"
date: 2009-06-30
forum: General Help
---

### Post by rockey191 on 2009-06-30
I want to run a program for finding closest pair of points in a given set. It is written with recursive calls. When i run the program some times it is giving the following error. help me .. its urgent..

pavan@pavan-laptop:~/ns/ject$ ./closestpair.out 50
*** glibc detected *** ./closestpair.out: corrupted double-linked list: 0x0804e9a8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7da8149]
/lib/tls/i686/cmov/libc.so.6[0xb7da988e]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7dad4f0]
./closestpair.out[0x80496cb]
./closestpair.out[0x8049498]
./closestpair.out[0x80497f6]
./closestpair.out[0x8049a71]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d54450]
./closestpair.out(__gxx_personality_v0+0x7d)[0x8048d21]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 07:00 103683 /home/pavan/ns/ject/closestpair.out
0804b000-0804c000 rw-p 00002000 07:00 103683 /home/pavan/ns/ject/closestpair.out
0804c000-0806d000 rw-p 0804c000 00:00 0 [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7d3d000-b7d3e000 rw-p b7d3d000 00:00 0 
b7d3e000-b7e87000 r-xp 00000000 07:00 152288 /lib/tls/i686/cmov/libc-2.7.so
b7e87000-b7e88000 r--p 00149000 07:00 152288 /lib/tls/i686/cmov/libc-2.7.so
b7e88000-b7e8a000 rw-p 0014a000 07:00 152288 /lib/tls/i686/cmov/libc-2.7.so
b7e8a000-b7e8d000 rw-p b7e8a000 00:00 0 
b7e8d000-b7e97000 r-xp 00000000 07:00 135458 /lib/libgcc_s.so.1
b7e97000-b7e98000 rw-p 0000a000 07:00 135458 /lib/libgcc_s.so.1
b7e98000-b7e99000 rw-p b7e98000 00:00 0 
b7e99000-b7ebc000 r-xp 00000000 07:00 152292 /lib/tls/i686/cmov/libm-2.7.so
b7ebc000-b7ebe000 rw-p 00023000 07:00 152292 /lib/tls/i686/cmov/libm-2.7.so
b7ebe000-b7fa6000 r-xp 00000000 07:01 57989 /usr/lib/libstdc++.so.6.0.9
b7fa6000-b7fa9000 r--p 000e8000 07:01 57989 /usr/lib/libstdc++.so.6.0.9
b7fa9000-b7fab000 rw-p 000eb000 07:01 57989 /usr/lib/libstdc++.so.6.0.9
b7fab000-b7fb1000 rw-p b7fab000 00:00 0 
b7fbf000-b7fc2000 rw-p b7fbf000 00:00 0 
b7fc2000-b7fc3000 r-xp b7fc2000 00:00 0 [vdso]
b7fc3000-b7fdd000 r-xp 00000000 07:00 135468 /lib/ld-2.7.so
b7fdd000-b7fdf000 rw-p 00019000 07:00 135468 /lib/ld-2.7.so
bfc92000-bfca7000 rw-p bffeb000 00:00 0 [stack]
Aborted

can someone explain why this error is coming and how to remove that error.

---

### Post by lsemmens on 2009-06-30
I do not know C++ but a code listing of the relevant routine may also assist.

---

### Post by lisati on 2009-06-30
hmmmm.....recursive subroutine/function calls..... Stack overflow on some sets of data that results in the routine seeing the "wrong" data, or the data being damaged?

I'm not particularly clued up on c++ either, but agree that perhaps a code snippet or two might help those who are better able to help.

---

### Post by rockey191 on 2009-06-30
when such type of errors results??

---

