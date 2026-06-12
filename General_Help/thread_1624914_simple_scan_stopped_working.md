---
title: "simple scan stopped working"
date: 2010-11-18
forum: General Help
---

### Post by zm38 on 2010-11-18
So until a few days ago, I was able to use simple scan to scan files onto my computer.  Now, for some reason, every time I start simple scan, it closes by itself after about three seconds. I tried running it from the terminal, and I got ```
*** buffer overflow detected ***: simple-scan terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0xb70ac390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0xb70ab2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe05fa)[0xb70aa5fa]
/usr/lib/sane/libsane-epson2.so.1(+0x121ad)[0xae2141ad]
/usr/lib/sane/libsane-epson2.so.1(+0x1257a)[0xae21457a]
/usr/lib/sane/libsane-epson2.so.1(sanei_configure_attach+0x495)[0xae207785]
/usr/lib/sane/libsane-epson2.so.1(+0x103b7)[0xae2123b7]
/usr/lib/sane/libsane-epson2.so.1(sane_epson2_get_devices+0x39)[0xae213f59]
/usr/lib/libsane.so.1(sane_dll_get_devices+0xb2)[0xb7127ea2]
/usr/lib/libsane.so.1(sane_get_devices+0x24)[0xb71259b4]
simple-scan[0x805a8c4]
/lib/libglib-2.0.so.0(+0x65def)[0xb7191def]
/lib/tls/i686/cmov/libpthread.so.0(+0x596e)[0xb781196e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7097a4e]
======= Memory map: ========
08048000-08062000 r-xp 00000000 08:07 4064271    /usr/bin/simple-scan
08062000-08063000 r--p 00019000 08:07 4064271    /usr/bin/simple-scan
08063000-08064000 rw-p 0001a000 08:07 4064271    /usr/bin/simple-scan
08223000-0842c000 rw-p 00000000 00:00 0          [heap]
ae1e3000-ae200000 r-xp 00000000 08:07 1572947    /lib/libgcc_s.so.1
ae200000-ae201000 r--p 0001c000 08:07 1572947    /lib/libgcc_s.so.1
ae201000-ae202000 rw-p 0001d000 08:07 1572947    /lib/libgcc_s.so.1
ae202000-ae229000 r-xp 00000000 08:07 4073099    /usr/lib/sane/libsane-epson2.so.1.0.20
ae229000-ae22a000 r--p 00026000 08:07 4073099    /usr/lib/sane/libsane-epson2.so.1.0.20
ae22a000-ae22b000 rw-p 00027000 08:07 4073099    /usr/lib/sane/libsane-epson2.so.1.0.20
ae22b000-ae22d000 rw-p 00000000 00:00 0 
ae22d000-ae250000 r-xp 00000000 08:07 4073102    /usr/lib/sane/libsane-fujitsu.so.1.0.20
ae250000-ae251000 r--p 00022000 08:07 4073102    /usr/lib/sane/libsane-fujitsu.so.1.0.20
ae251000-ae252000 rw-p 00023000 08:07 4073102    /usr/lib/sane/libsane-fujitsu.so.1.0.20
ae252000-ae253000 rw-p 00000000 00:00 0 
ae253000-ae283000 r-xp 00000000 08:07 4073105    /usr/lib/sane/libsane-genesys.so.1.0.20
ae283000-ae284000 r--p 0002f000 08:07 4073105    /usr/lib/sane/libsane-genesys.so.1.0.20
ae284000-ae288000 rw-p 00030000 08:07 4073105    /usr/lib/sane/libsane-genesys.so.1.0.20
ae288000-ae28a000 rw-p 00000000 00:00 0 
ae28a000-ae2a8000 r-xp 00000000 08:07 4073111    /usr/lib/sane/libsane-gt68xx.so.1.0.20
ae2a8000-ae2a9000 r--p 0001d000 08:07 4073111    /usr/lib/sane/libsane-gt68xx.so.1.0.20
ae2a9000-ae2ac000 rw-p 0001e000 08:07 4073111    /usr/lib/sane/libsane-gt68xx.so.1.0.20
ae2ac000-ae2ae000 rw-p 00000000 00:00 0 
ae2ae000-ae2d4000 r-xp 00000000 08:07 4073114    /usr/lib/sane/libsane-hp.so.1.0.20
ae2d4000-ae2d6000 r--p 00025000 08:07 4073114    /usr/lib/sane/libsane-hp.so.1.0.20
ae2d6000-ae2d7000 rw-p 00027000 08:07 4073114    /usr/lib/sane/libsane-hp.so.1.0.20
ae2d7000-ae2d9000 rw-p 00000000 00:00 0 
ae2d9000-ae2f8000 r-xp 00000000 08:07 4066700    /usr/lib/libjpeg.so.62.0.0
ae2f8000-ae2f9000 r--p 0001e000 08:07 4066700    /usr/lib/libjpeg.so.62.0.0
ae2f9000-ae2fa000 rw-p 0001f000 08:07 4066700    /usr/lib/libjpeg.so.62.0.0
ae2fa000-ae352000 r-xp 00000000 08:07 4064960    /usr/lib/libtiff.so.4.3.2
ae352000-ae354000 r--p 00057000 08:07 4064960    /usr/lib/libtiff.so.4.3.2
ae354000-ae355000 rw-p 00059000 08:07 4064960    /usr/lib/libtiff.so.4.3.2
ae369000-ae3cd000 r-xp 00000000 08:07 4073120    /usr/lib/sane/libsane-hp3900.so.1.0.20
ae3cd000-ae3ce000 r--p 00063000 08:07 4073120    /usr/lib/sane/libsane-hp3900.so.1.0.20
ae3ce000-ae3cf000 rw-p 00064000 08:07 4073120    /usr/lib/sane/libsane-hp3900.so.1.0.20
ae3cf000-ae3d1000 rw-p 00000000 00:00 0 
ae3d1000-ae3d8000 r-xp 00000000 08:07 4073137    /usr/lib/sane/libsane-hpsj5s.so.1.0.20
ae3d8000-ae3d9000 r--p 00006000 08:07 4073137    /usr/lib/sane/libsane-hpsj5s.so.1.0.20
ae3d9000-ae3db000 rw-p 00007000 08:07 4073137    /usr/lib/sane/libsane-hpsj5s.so.1.0.20
ae3db000-ae3eb000 r-xp 00000000 08:07 4073117    /usr/lib/sane/libsane-hp3500.so.1.0.20
ae3eb000-ae3ec000 r--p 0000f000 08:07 4073117    /usr/lib/sane/libsane-hp3500.so.1.0.20
ae3ec000-ae3ed000 rw-p 00010000 08:07 4073117    /usr/lib/sane/libsane-hp3500.so.1.0.20
ae3ed000-ae40f000 rw-p 00000000 00:00 0 
ae40f000-ae41e000 r-xp 00000000 08:07 4073123    /usr/lib/sane/libsane-hp4200.so.1.0.20
ae41e000-ae41f000 r--p 0000e000 08:07 4073123    /usr/lib/sane/libsane-hp4200.so.1.0.20
ae41f000-ae420000 rw-p 0000f000 08:07 4073123    /usr/lib/sane/libsane-hp4200.so.1.0.20
ae420000-ae421000 rw-p 00000000 00:00 0 
ae421000-ae42e000 r-xp 00000000 08:07 4073126    /usr/lib/sane/libsane-hp5400.so.1.0.20
ae42e000-ae42f000 r--p 0000c000 08:07 4073126    /usr/lib/sane/libsane-hp5400.so.1.0.20
ae42f000-ae430000 rw-p 0000d000 08:07 4073126    /usr/lib/sane/libsane-hp5400.so.1.0.20
ae430000-ae431000 rw-p 00000000 00:00 0 
ae431000-ae442000 r-xp 00000000 08:07 4073129    /usr/lib/sane/libsane-hp5590.so.1.0.20
ae442000-ae443000 r--p 00010000 08:07 4073129    /usr/lib/sane/libsane-hp5590.so.1.0.20
ae443000-ae444000 rw-p 00011000 08:07 4073129    /usr/lib/sane/libsane-hp5590.so.1.0.20
ae444000-ae445000 rw-p 00000000 00:00 0 
ae445000-ae450000 r-xp 00000000 08:07 4073134    /usr/lib/sane/libsane-hpljm1005.so.1.0.20
ae450000-ae451000 r--p 0000b000 08:07 4073134    /usr/lib/sane/libsane-hpljm1005.so.1.0.20
ae451000-ae452000 rw-p 0000c000 08:07 4073134    /usr/lib/sane/libsane-hpljm1005.so.1.0.20
ae452000-ae453000 rw-p 00000000 00:00 0 
ae453000-ae46d000 r-xp 00000000 08:07 4073140    /usr/lib/sane/libsane-hs2p.so.1.0.20
ae46d000-ae46e000 r--p 00019000 08:07 4073140    /usr/lib/sane/libsane-hs2p.so.1.0.20
ae46e000-ae46f000 rw-p 0001a000 08:07 4073140    /usr/lib/sane/libsane-hs2p.so.1.0.20
ae46f000-ae47c000 r-xp 00000000 08:07 4073143    /usr/lib/sane/libsane-ibm.so.1.0.20
ae47c000-ae47d000 r--p 0000c000 08:07 4073143    /usr/lib/sane/libsane-ibm.so.1.0.20
ae47d000-ae47e000 rw-p 0000d000 08:07 4073143    /usr/lib/sane/libsane-ibm.so.1.0.20
ae47e000-ae48c000 r-xp 00000000 08:07 4073146    /usr/lib/sane/libsane-leo.so.1.0.20
ae48c000-ae48d000 r--p 0000d000 08:07 4073146    /usr/lib/sane/libsane-leo.so.1.0.20
ae48d000-ae48e000 rw-p 0000e000 08:07 4073146    /usr/lib/sane/libsane-leo.so.1.0.20
ae48e000-ae4a2000 r-xp 00000000 08:07 4073149    /usr/lib/sane/libsane-lexmark.so.1.0.20
ae4a2000-ae4a3000 r--p 00013000 08:07 4073149    /usr/lib/sane/libsane-lexmark.so.1.0.20
ae4a3000-ae4a4000 rw-p 00014000 08:07 4073149    /usr/lib/sane/libsane-lexmark.so.1.0.20
ae4a4000-ae4a6000 rw-p 00000000 00:00 0 
ae4a6000-ae4b5000 r-xp 00000000 08:07 4073152    /usr/lib/sane/libsane-ma1509.so.1.0.20
ae4b5000-ae4b6000 r--p 0000e000 08:07 4073152    /usr/lib/sane/libsane-ma1509.so.1.0.20Aborted

```I don't really know what this means, but I was hoping that someone who did could help me figure out how to fix this.

I am running Ubuntu 10.04 LTS on a Dell Inspiron 1545 laptop, and I am using a Lexmark x2600 all-in-one printer/scanner/copier.  I currently have simple scan version 1.0.3-0ubuntu1 installed.

Any and all help would be greatly appreciated!  Thanks in advance!

---

### Post by zm38 on 2010-12-05
So, I don't really know what happened, but suddenly it works now....Magic?

Still, if anyone has any ideas as to what the problem was in the first place, I'd love to hear them.

---

