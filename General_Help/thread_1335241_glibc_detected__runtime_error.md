---
title: "*** glibc detected *** runtime error"
date: 2009-11-23
forum: General Help
---

### Post by abhishekdey1985 on 2009-11-23
>Hi i'm new to CUDA. I wrote a simple CUDA program. When executing it the program throws the following runtime exception when calling Free(). cudaFree() returns well with no problem. I'm unable to resolve the problem. Need urgent help.

>Also can somebody explain what does this exception means?

(I'm running Ubuntu 9.10 Karmic Koala 64-bit. Using CUDA 2.3 64-bit and NVIDIA 190.42 Driver)

```

*** glibc detected *** ./a.out: free(): invalid next size (fast): 0x0000000001038210 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f71c4523dd6]
/lib/libc.so.6(cfree+0x6c)[0x7f71c452870c]
./a.out[0x401157]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f71c44ccabd]
./a.out[0x400ea9]
======= Memory map: ========
00400000-00414000 r-xp 00000000 08:12 129140                             /home/abhishek/Programming/CUDA/a.out
00613000-00614000 r--p 00013000 08:12 129140                             /home/abhishek/Programming/CUDA/a.out
00614000-00615000 rw-p 00014000 08:12 129140                             /home/abhishek/Programming/CUDA/a.out
01038000-01087000 rw-p 00000000 00:00 0                                  [heap]
7f71bc000000-7f71bc021000 rw-p 00000000 00:00 0 
7f71bc021000-7f71c0000000 ---p 00000000 00:00 0 
7f71c2bcb000-7f71c2bcc000 rw-p 00000000 00:00 0 
7f71c2bcc000-7f71c2ccc000 rw-s 49f54000 00:0f 6319                       /dev/nvidia0
7f71c2ccc000-7f71c2dcc000 rw-s 49e51000 00:0f 6319                       /dev/nvidia0
7f71c2dcc000-7f71c2ecc000 rw-s 49d4e000 00:0f 6319                       /dev/nvidia0
7f71c2ecc000-7f71c2fcc000 rw-s 49c48000 00:0f 6319                       /dev/nvidia0
7f71c2fcc000-7f71c2fcd000 rw-s 49c44000 00:0f 6319                       /dev/nvidia0
7f71c2fcd000-7f71c2fce000 rw-s f2c0a000 00:0f 6319                       /dev/nvidia0
7f71c2fce000-7f71c2fcf000 rw-s 49c43000 00:0f 6319                       /dev/nvidia0
7f71c2fcf000-7f71c33d1000 rw-s 4c09a000 00:0f 6319                       /dev/nvidia0
7f71c33d1000-7f71c37d3000 rw-s 4e5c6000 00:0f 6319                       /dev/nvidia0
7f71c37d3000-7f71c37e9000 r-xp 00000000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c37e9000-7f71c39e8000 ---p 00016000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c39e8000-7f71c39e9000 r--p 00015000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c39e9000-7f71c39ea000 rw-p 00016000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c39ea000-7f71c3d23000 r-xp 00000000 08:12 5088                       /usr/lib/libcuda.so.190.42
7f71c3d23000-7f71c3e22000 ---p 00339000 08:12 5088                       /usr/lib/libcuda.so.190.42
7f71c3e22000-7f71c3e5e000 rw-p 00338000 08:12 5088                       /usr/lib/libcuda.so.190.42
7f71c3e5e000-7f71c3e86000 rw-p 00000000 00:00 0 
7f71c3e86000-7f71c3e8d000 r-xp 00000000 08:12 2291                       /lib/librt-2.10.1.so
7f71c3e8d000-7f71c408c000 ---p 00007000 08:12 2291                       /lib/librt-2.10.1.so
7f71c408c000-7f71c408d000 r--p 00006000 08:12 2291                       /lib/librt-2.10.1.so
7f71c408d000-7f71c408e000 rw-p 00007000 08:12 2291                       /lib/librt-2.10.1.so
7f71c408e000-7f71c40a5000 r-xp 00000000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c40a5000-7f71c42a4000 ---p 00017000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c42a4000-7f71c42a5000 r--p 00016000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c42a5000-7f71c42a6000 rw-p 00017000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c42a6000-7f71c42aa000 rw-p 00000000 00:00 0 
7f71c42aa000-7f71c42ac000 r-xp 00000000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c42ac000-7f71c44ac000 ---p 00002000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c44ac000-7f71c44ad000 r--p 00002000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c44ad000-7f71c44ae000 rw-p 00003000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c44ae000-7f71c4614000 r-xp 00000000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4614000-7f71c4813000 ---p 00166000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4813000-7f71c4817000 r--p 00165000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4817000-7f71c4818000 rw-p 00169000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4818000-7f71c481d000 rw-p 00000000 00:00 0 
7f71c481d000-7f71c4833000 r-xp 00000000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4833000-7f71c4a32000 ---p 00016000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4a32000-7f71c4a33000 r--p 00015000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4a33000-7f71c4a34000 rw-p 00016000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4a34000-7f71c4ab6000 r-xp 00000000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4ab6000-7f71c4cb6000 ---p 00082000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4cb6000-7f71c4cb7000 r--p 00082000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4cb7000-7f71c4cb8000 rw-p 00083000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4cb8000-7f71c4daa000 r-xp 00000000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4daa000-7f71c4faa000 ---p 000f2000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4faa000-7f71c4fb1000 r--p 000f2000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4fb1000-7f71c4fb3000 rw-p 000f9000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4fb3000-7f71c4fc8000 rw-p 00000000 00:00 0 
7f71c4fc8000-7f71c5006000 r-xp 00000000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5006000-7f71c5206000 ---p 0003e000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5206000-7f71c5207000 r--p 0003e000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5207000-7f71c5208000 rw-p 0003f000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5208000-7f71c5227000 r-xp 00000000 08:12 2173                       /lib/ld-2.10.1.so
7f71c53fe000-7f71c540f000 rw-s 4e58d000 00:0f 6319                       /dev/nvidia0
7f71c540f000-7f71c5414000 rw-p 00000000 00:00 0 
7f71c5420000-7f71c5421000 rw-s f2c08000 00:0f 6319                       /dev/nvidia0
7f71c5421000-7f71c5422000 rw-s 4c091000 00:0f 6319                       /dev/nvidia0
7f71c5422000-7f71c5423000 r--s f2009000 00:0f 6319                       /dev/nvidia0
7f71c5423000-7f71c5426000 rw-p 00000000 00:00 0 
7f71c5426000-7f71c5427000 r--p 0001e000 08:12 2173                       /lib/ld-2.10.1.so
7f71c5427000-7f71c5428000 rw-p 0001f000 08:12 2173                       /lib/ld-2.10.1.so
Aborted

```

---

### Post by karlson on 2009-11-23
> **abhishekdey1985 said:**
> >Hi i'm new to CUDA. I wrote a simple CUDA program. When executing it the program throws the following runtime exception when calling Free(). cudaFree() returns well with no problem. I'm unable to resolve the problem. Need urgent help.

>Also can somebody explain what does this exception means?

(I'm running Ubuntu 9.10 Karmic Koala 64-bit. Using CUDA 2.3 64-bit and NVIDIA 190.42 Driver)

```

*** glibc detected *** ./a.out: free(): invalid next size (fast): 0x0000000001038210 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f71c4523dd6]
/lib/libc.so.6(cfree+0x6c)[0x7f71c452870c]
./a.out[0x401157]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f71c44ccabd]
./a.out[0x400ea9]
======= Memory map: ========
00400000-00414000 r-xp 00000000 08:12 129140                             /home/abhishek/Programming/CUDA/a.out
00613000-00614000 r--p 00013000 08:12 129140                             /home/abhishek/Programming/CUDA/a.out
00614000-00615000 rw-p 00014000 08:12 129140                             /home/abhishek/Programming/CUDA/a.out
01038000-01087000 rw-p 00000000 00:00 0                                  [heap]
7f71bc000000-7f71bc021000 rw-p 00000000 00:00 0 
7f71bc021000-7f71c0000000 ---p 00000000 00:00 0 
7f71c2bcb000-7f71c2bcc000 rw-p 00000000 00:00 0 
7f71c2bcc000-7f71c2ccc000 rw-s 49f54000 00:0f 6319                       /dev/nvidia0
7f71c2ccc000-7f71c2dcc000 rw-s 49e51000 00:0f 6319                       /dev/nvidia0
7f71c2dcc000-7f71c2ecc000 rw-s 49d4e000 00:0f 6319                       /dev/nvidia0
7f71c2ecc000-7f71c2fcc000 rw-s 49c48000 00:0f 6319                       /dev/nvidia0
7f71c2fcc000-7f71c2fcd000 rw-s 49c44000 00:0f 6319                       /dev/nvidia0
7f71c2fcd000-7f71c2fce000 rw-s f2c0a000 00:0f 6319                       /dev/nvidia0
7f71c2fce000-7f71c2fcf000 rw-s 49c43000 00:0f 6319                       /dev/nvidia0
7f71c2fcf000-7f71c33d1000 rw-s 4c09a000 00:0f 6319                       /dev/nvidia0
7f71c33d1000-7f71c37d3000 rw-s 4e5c6000 00:0f 6319                       /dev/nvidia0
7f71c37d3000-7f71c37e9000 r-xp 00000000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c37e9000-7f71c39e8000 ---p 00016000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c39e8000-7f71c39e9000 r--p 00015000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c39e9000-7f71c39ea000 rw-p 00016000 08:12 2325                       /lib/libz.so.1.2.3.3
7f71c39ea000-7f71c3d23000 r-xp 00000000 08:12 5088                       /usr/lib/libcuda.so.190.42
7f71c3d23000-7f71c3e22000 ---p 00339000 08:12 5088                       /usr/lib/libcuda.so.190.42
7f71c3e22000-7f71c3e5e000 rw-p 00338000 08:12 5088                       /usr/lib/libcuda.so.190.42
7f71c3e5e000-7f71c3e86000 rw-p 00000000 00:00 0 
7f71c3e86000-7f71c3e8d000 r-xp 00000000 08:12 2291                       /lib/librt-2.10.1.so
7f71c3e8d000-7f71c408c000 ---p 00007000 08:12 2291                       /lib/librt-2.10.1.so
7f71c408c000-7f71c408d000 r--p 00006000 08:12 2291                       /lib/librt-2.10.1.so
7f71c408d000-7f71c408e000 rw-p 00007000 08:12 2291                       /lib/librt-2.10.1.so
7f71c408e000-7f71c40a5000 r-xp 00000000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c40a5000-7f71c42a4000 ---p 00017000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c42a4000-7f71c42a5000 r--p 00016000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c42a5000-7f71c42a6000 rw-p 00017000 08:12 2284                       /lib/libpthread-2.10.1.so
7f71c42a6000-7f71c42aa000 rw-p 00000000 00:00 0 
7f71c42aa000-7f71c42ac000 r-xp 00000000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c42ac000-7f71c44ac000 ---p 00002000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c44ac000-7f71c44ad000 r--p 00002000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c44ad000-7f71c44ae000 rw-p 00003000 08:12 2211                       /lib/libdl-2.10.1.so
7f71c44ae000-7f71c4614000 r-xp 00000000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4614000-7f71c4813000 ---p 00166000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4813000-7f71c4817000 r--p 00165000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4817000-7f71c4818000 rw-p 00169000 08:12 2197                       /lib/libc-2.10.1.so
7f71c4818000-7f71c481d000 rw-p 00000000 00:00 0 
7f71c481d000-7f71c4833000 r-xp 00000000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4833000-7f71c4a32000 ---p 00016000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4a32000-7f71c4a33000 r--p 00015000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4a33000-7f71c4a34000 rw-p 00016000 08:12 2223                       /lib/libgcc_s.so.1
7f71c4a34000-7f71c4ab6000 r-xp 00000000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4ab6000-7f71c4cb6000 ---p 00082000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4cb6000-7f71c4cb7000 r--p 00082000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4cb7000-7f71c4cb8000 rw-p 00083000 08:12 2239                       /lib/libm-2.10.1.so
7f71c4cb8000-7f71c4daa000 r-xp 00000000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4daa000-7f71c4faa000 ---p 000f2000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4faa000-7f71c4fb1000 r--p 000f2000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4fb1000-7f71c4fb3000 rw-p 000f9000 08:12 9519                       /usr/lib/libstdc++.so.6.0.13
7f71c4fb3000-7f71c4fc8000 rw-p 00000000 00:00 0 
7f71c4fc8000-7f71c5006000 r-xp 00000000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5006000-7f71c5206000 ---p 0003e000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5206000-7f71c5207000 r--p 0003e000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5207000-7f71c5208000 rw-p 0003f000 08:12 138540                     /usr/local/cuda/lib64/libcudart.so.2.3
7f71c5208000-7f71c5227000 r-xp 00000000 08:12 2173                       /lib/ld-2.10.1.so
7f71c53fe000-7f71c540f000 rw-s 4e58d000 00:0f 6319                       /dev/nvidia0
7f71c540f000-7f71c5414000 rw-p 00000000 00:00 0 
7f71c5420000-7f71c5421000 rw-s f2c08000 00:0f 6319                       /dev/nvidia0
7f71c5421000-7f71c5422000 rw-s 4c091000 00:0f 6319                       /dev/nvidia0
7f71c5422000-7f71c5423000 r--s f2009000 00:0f 6319                       /dev/nvidia0
7f71c5423000-7f71c5426000 rw-p 00000000 00:00 0 
7f71c5426000-7f71c5427000 r--p 0001e000 08:12 2173                       /lib/ld-2.10.1.so
7f71c5427000-7f71c5428000 rw-p 0001f000 08:12 2173                       /lib/ld-2.10.1.so
Aborted

```

This means that you accessing memory that doesn't belong to the program.  Can happen if the library for compile doesn't match the library at runtime.  Or you actually call the free twice on the object.

You might want to do gdb ./a.out <corefile> to see where this actually happens.

---

### Post by abhishekdey1985 on 2009-11-23
The funny thing is that i have allocated only one pointer variable of type float using malloc() and releasing the same at the end using Free(). If i remove all Free calls, the program doesn't throw the exception. But even a single Free() call makes Kernel to throw SIGABRT signal.

I tried using GDB and it shows me the following:

0x00007ffff70b84b5 in raise () from /lib/libc.so.6

I guess raise() in libc raises signals (Such as SIGABRT, etc)...if i'm not wrong!!
Still coudn't figure out the problem!!

---

