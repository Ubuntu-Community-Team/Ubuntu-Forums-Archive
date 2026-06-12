---
title: "*buffer overflow detected* make[2]:[libgcc.a] Aborted make[2]:Deleting file libgcc2.c"
date: 2011-04-29
forum: General Help
---

### Post by aravindreddy on 2011-04-29
Hello All

I am trying to build sescutils on my Ubuntu 10.04 using gcc-4.4. When I build the build-2-gcc-core, I get the following error- ***** buffer overflow detected *****.

I see that the error is due to the inability of libgcc2.c to be compiled by gcc-4.4. Because the libgcc2.c I am compiling is an old one and was meant to be compiled by gcc-3.4as I compile with gcc-4.4 because other files are to be compiled by gcc-4.4 only.

Can any body provide me with a libgcc2.c which can be compiled by gcc-4.4. 

Or if my inference is wrong, can anybody correct me.

[B]*** buffer overflow detected ***: mipseb-linux-ar terminated
[/B]======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x2b4628467217]
/lib/libc.so.6(+0xfe0d0)[0x2b46284660d0]
/lib/libc.so.6(+0xfd539)[0x2b4628465539]
/lib/libc.so.6(_IO_default_xsputn+0xcc)[0x2b46283ddd1c]
/lib/libc.so.6(_IO_padn+0xe8)[0x2b46283d17f8]
/lib/libc.so.6(_IO_vfprintf+0x2afc)[0x2b46283afe9c]
/lib/libc.so.6(__vsprintf_chk+0x99)[0x2b46284655d9]
/lib/libc.so.6(__sprintf_chk+0x7f)[0x2b462846551f]
mipseb-linux-ar[0x409d04]
mipseb-linux-ar[0x407f41]
mipseb-linux-ar[0x40a5ad]
mipseb-linux-ar[0x41143f]
mipseb-linux-ar[0x40483f]
mipseb-linux-ar[0x404d0d]
mipseb-linux-ar[0x4057d6]
/lib/libc.so.6(__libc_start_main+0xfd)[0x2b4628386c4d]
mipseb-linux-ar[0x401f59]
======= Memory map: ========
00400000-00490000 r-xp 00000000 08:07 1199964                            /home/anusha/sescutils/install/bin/mipseb-linux-ar
0068f000-00690000 r--p 0008f000 08:07 1199964                            /home/anusha/sescutils/install/bin/mipseb-linux-ar
00690000-00691000 rw-p 00090000 08:07 1199964                            /home/anusha/sescutils/install/bin/mipseb-linux-ar
00691000-00696000 rw-p 00000000 00:00 0 
00df8000-01359000 rw-p 00000000 00:00 0                                  [heap]
2b4628146000-2b4628166000 r-xp 00000000 08:07 3932181                    /lib/ld-2.11.1.so
2b4628166000-2b4628168000 rw-p 00000000 00:00 0 
2b4628168000-2b4628169000 r--p 00000000 08:07 922651                     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2b4628169000-2b4628170000 r--s 00000000 08:07 793029                     /usr/lib/gconv/gconv-modules.cache
2b4628170000-2b46281af000 r--p 00000000 08:07 794320                     /usr/lib/locale/en_US.utf8/LC_CTYPE
2b46281af000-2b46281b9000 rw-p 00000000 00:00 0 
2b4628365000-2b4628366000 r--p 0001f000 08:07 3932181                    /lib/ld-2.11.1.so
2b4628366000-2b4628367000 rw-p 00020000 08:07 3932181                    /lib/ld-2.11.1.so
2b4628367000-2b4628368000 rw-p 00000000 00:00 0 
2b4628368000-2b46284e2000 r-xp 00000000 08:07 3932205                    /lib/libc-2.11.1.so
2b46284e2000-2b46286e1000 ---p 0017a000 08:07 3932205                    /lib/libc-2.11.1.so
2b46286e1000-2b46286e5000 r--p 00179000 08:07 3932205                    /lib/libc-2.11.1.so
2b46286e5000-2b46286e6000 rw-p 0017d000 08:07 3932205                    /lib/libc-2.11.1.so
2b46286e6000-2b46286ed000 rw-p 00000000 00:00 0 
2b46286ed000-2b4628703000 r-xp 00000000 08:07 3932239                    /lib/libgcc_s.so.1
2b4628703000-2b4628902000 ---p 00016000 08:07 3932239                    /lib/libgcc_s.so.1
2b4628902000-2b4628903000 r--p 00015000 08:07 3932239                    /lib/libgcc_s.so.1
2b4628903000-2b4628904000 rw-p 00016000 08:07 3932239                    /lib/libgcc_s.so.1
7fff36274000-7fff3628b000 rw-p 00000000 00:00 0                          [stack]
7fff363ff000-7fff36400000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
[B]make[2]: *** [libgcc.a] Aborted
make[2]: *** Deleting file `libgcc.a'
make[2]: Leaving directory `/home/anusha/sescutils/build-mipseb-linux/obj/gcc-core-build/gcc'
make[1]: *** [libgcc.a] Error 2
make[1]: Leaving directory `/home/anusha/sescutils/build-mipseb-linux/obj/gcc-core-build/gcc'
make: *** [all-gcc] Error 2
[/B]
Thanks in advance,
Aravind.

---

