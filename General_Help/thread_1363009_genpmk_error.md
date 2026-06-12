---
title: "genpmk error"
date: 2009-12-23
forum: General Help
---

### Post by sem1845 on 2009-12-23
trying to make new wpa table and genpmk is giving me this

```
eli@ubuntu:~$ genpmk -f final-wordlist.txt -d docgirl -s doctorgirl
genpmk 1.0 - WPA-PSK precomputation attack. <jwright@hasborg.com>
File docgirl exists, appending new data.
*** buffer overflow detected ***: genpmk terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x430de8]
/lib/tls/i686/cmov/libc.so.6[0x42fe20]
genpmk[0x8049c41]
genpmk[0x8049f5c]
genpmk[0x804a0b0]
genpmk[0x80491ea]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x366b56]
genpmk[0x8048b61]
======= Memory map: ========
0011b000-0026a000 r-xp 00000000 07:00 1867       /lib/i686/cmov/libcrypto.so.0.9.8
0026a000-00272000 r--p 0014e000 07:00 1867       /lib/i686/cmov/libcrypto.so.0.9.8
00272000-0027f000 rw-p 00156000 07:00 1867       /lib/i686/cmov/libcrypto.so.0.9.8
0027f000-00283000 rw-p 00000000 00:00 0 
00350000-0048e000 r-xp 00000000 07:00 4861       /lib/tls/i686/cmov/libc-2.10.1.so
0048e000-00490000 r--p 0013e000 07:00 4861       /lib/tls/i686/cmov/libc-2.10.1.so
00490000-00491000 rw-p 00140000 07:00 4861       /lib/tls/i686/cmov/libc-2.10.1.so
00491000-00494000 rw-p 00000000 00:00 0 
004a1000-004bd000 r-xp 00000000 07:00 1503       /lib/libgcc_s.so.1
004bd000-004be000 r--p 0001b000 07:00 1503       /lib/libgcc_s.so.1
004be000-004bf000 rw-p 0001c000 07:00 1503       /lib/libgcc_s.so.1
0051f000-00520000 r-xp 00000000 00:00 0          [vdso]
0068b000-0069f000 r-xp 00000000 07:00 1605       /lib/libz.so.1.2.3.3
0069f000-006a0000 r--p 00013000 07:00 1605       /lib/libz.so.1.2.3.3
006a0000-006a1000 rw-p 00014000 07:00 1605       /lib/libz.so.1.2.3.3
006c0000-006c2000 r-xp 00000000 07:00 4867       /lib/tls/i686/cmov/libdl-2.10.1.so
006c2000-006c3000 r--p 00001000 07:00 4867       /lib/tls/i686/cmov/libdl-2.10.1.so
006c3000-006c4000 rw-p 00002000 07:00 4867       /lib/tls/i686/cmov/libdl-2.10.1.so
009e8000-00a03000 r-xp 00000000 07:00 1453       /lib/ld-2.10.1.so
00a03000-00a04000 r--p 0001a000 07:00 1453       /lib/ld-2.10.1.so
00a04000-00a05000 rw-p 0001b000 07:00 1453       /lib/ld-2.10.1.so
00d6d000-00d9e000 r-xp 00000000 07:00 8684       /usr/lib/libpcap.so.1.0.0
00d9e000-00d9f000 r--p 00031000 07:00 8684       /usr/lib/libpcap.so.1.0.0
00d9f000-00da0000 rw-p 00032000 07:00 8684       /usr/lib/libpcap.so.1.0.0
08048000-0804b000 r-xp 00000000 07:00 102920     /usr/local/bin/genpmk
0804b000-0804c000 r--p 00002000 07:00 102920     /usr/local/bin/genpmk
0804c000-0804d000 rw-p 00003000 07:00 102920     /usr/local/bin/genpmk
09964000-09985000 rw-p 00000000 00:00 0          [heap]
b7878000-b787a000 rw-p 00000000 00:00 0 
b7885000-b788a000 rw-p 00000000 00:00 0 
bffa8000-bffbd000 rw-p 00000000 00:00 0          [stack]
Aborted
eli@ubuntu:~$ 

```

---

### Post by sem1845 on 2009-12-23
this is creating the docgirl file that is 40 bytes and can't be opened bc it says it is an unknown file type

---

### Post by sem1845 on 2009-12-24
fixed with this patch
[http://question-defense.com/2009/12/24/cowpatty-buffer-overflow](http://question-defense.com/2009/12/24/cowpatty-buffer-overflow)

---

