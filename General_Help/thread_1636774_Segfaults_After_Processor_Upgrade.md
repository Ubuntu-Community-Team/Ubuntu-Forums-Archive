---
title: "Segfaults After Processor Upgrade"
date: 2010-12-03
forum: General Help
---

### Post by TaterSalad22 on 2010-12-03
Hi All,

I upgraded my processor two days ago(p4 -> C2D), and ever since then I have been getting segfaults, which are causing my programs to crash randomly. At first I thought it was isolated to one program(deluge), but after searching around I was looking at the /var/log/messages and found a bunch of segfault messages after I installaed the processor. Here is the grep from the messages file:

```
Nov 29 12:35:03 Thor kernel: [66065.114231] npviewer.bin[14952]: segfault at 0 ip 00000000f6232ed1 sp 00000000ffe9e6d0 error 4 in libflashplayer.so[f5e93000+b2e000]
Nov 29 12:41:23 Thor kernel: [66445.260799] npviewer.bin[15324]: segfault at 418 ip 00000000f60ddc86 sp 00000000ffb4b928 error 6 in libflashplayer.so[f5e8e000+b2e000]
Nov 29 20:05:04 Thor kernel: [ 2302.330752] npviewer.bin[2872]: segfault at 418 ip 00000000f6085c86 sp 00000000ffd9b9d8 error 6 in libflashplayer.so[f5e36000+b2e000]
Nov 29 20:05:24 Thor kernel: [ 2322.225667] npviewer.bin[2890]: segfault at f403604c ip 00000000f61b3ee7 sp 00000000ff86d7d0 error 4 in libflashplayer.so[f5e14000+b2e000]
Nov 29 20:05:47 Thor kernel: [ 2344.425995] npviewer.bin[2913]: segfault at 418 ip 00000000f6022c86 sp 00000000fff52278 error 6 in libflashplayer.so[f5dd3000+b2e000]
Nov 30 22:21:37 Thor kernel: [  115.574538] /usr/bin/deluge[2033]: segfault at 31e3cd8 ip 00000000031e3cd8 sp 00007fffb2268588 error 15
Nov 30 22:34:01 Thor kernel: [   83.490986] /usr/bin/deluge[2090]: segfault at 0 ip (null) sp 00007fff76975af8 error 14 in python2.6[400000+21a000]
Dec  1 00:01:58 Thor kernel: [ 4983.145781] /usr/bin/deluge[3533]: segfault at 828f40 ip 0000000000828f40 sp 00007fff68514d08 error 15 in python2.6[81a000+62000]
Dec  1 00:02:32 Thor kernel: [ 5017.417788] /usr/bin/deluge[3660]: segfault at 0 ip (null) sp 00007fffd9653b58 error 14 in python2.6[400000+21a000]
Dec  1 00:12:07 Thor kernel: [ 5592.973621] /usr/bin/deluge[3841]: segfault at 0 ip (null) sp 00007fff1c0e6a88 error 14 in python2.6[400000+21a000]
Dec  1 00:27:41 Thor kernel: [ 6526.089930] python[4915]: segfault at 0 ip (null) sp 00007fff200d7558 error 14 in python2.6[400000+21a000]
Dec  1 00:34:22 Thor kernel: [  222.950847] python[2781]: segfault at 0 ip (null) sp 00007fff27642088 error 14 in python2.6[400000+21a000]
Dec  1 00:38:13 Thor kernel: [  453.425553] chromium-browse[2825]: segfault at 110018 ip 00007f8a3a48245d sp 00007fff1c99f800 error 4 in chromium-browser[7f8a390a0000+2e96000]
Dec  1 00:43:50 Thor kernel: [  790.794381] chromium-browse[2833]: segfault at 7f8a3f195fe0 ip 00007f8a3f195fe0 sp 00007fff1c99f0b8 error 15
Dec  1 00:51:03 Thor kernel: [ 1223.052356] npviewer.bin[2762]: segfault at 0 ip 00000000f61a8ed1 sp 00000000ffe65090 error 4 in libflashplayer.so[f5e09000+b2e000]
Dec  1 00:56:54 Thor kernel: [ 1574.350811] npviewer.bin[3067]: segfault at 418 ip 00000000f600fc86 sp 00000000ff820778 error 6 in libflashplayer.so[f5dc0000+b2e000]
Dec  1 01:07:11 Thor kernel: [ 2191.457293] npviewer.bin[3131]: segfault at f323d256 ip 00000000f5f0e5c3 sp 00000000ffebdd50 error 4 in libflashplayer.so[f5eb5000+b2e000]
Dec  1 01:09:14 Thor kernel: [ 2314.307376] python[3294]: segfault at 13 ip 000000000047e0c8 sp 00007fff62d0c768 error 4 in python2.6[400000+21a000]
Dec  1 01:42:17 Thor kernel: [ 4297.248816] npviewer.bin[3601]: segfault at 56a ip 00000000f6020a90 sp 00000000ff930780 error 4 in libflashplayer.so[f5dc3000+b2e000]
Dec  1 01:54:43 Thor kernel: [ 5043.694911] python[3876]: segfault at 0 ip (null) sp 00007fff70169098 error 14 in python2.6[400000+21a000]
Dec  1 02:09:53 Thor kernel: [ 5953.456882] npviewer.bin[3653]: segfault at 56a ip 00000000f60d9a90 sp 00000000ff87ca10 error 4 in libflashplayer.so[f5e7c000+b2e000]
Dec  1 02:35:00 Thor kernel: [  297.390905] npviewer.bin[2462]: segfault at 81f3ffd0 ip 0000000081f3ffd0 sp 00000000ffccc32c error 14
Dec  1 02:40:50 Thor kernel: [  647.669805] npviewer.bin[2543]: segfault at 0 ip (null) sp 00000000ffb3919c error 14 in npviewer.bin[8048000+1f000]
Dec  1 02:40:56 Thor kernel: [  653.933588] python[2893]: segfault at 0 ip (null) sp 00007fffc5c76bc8 error 14 in python2.6[400000+21a000]
Dec  1 02:41:04 Thor kernel: [  661.483957] python[2920]: segfault at 7f55dffb1570 ip 00007f55dffb1570 sp 00007fff5bbe9838 error 15
Dec  1 02:42:07 Thor kernel: [  724.105739] npviewer.bin[2903]: segfault at f579304c ip 00000000f6174ee7 sp 00000000ff8f5200 error 4 in libflashplayer.so[f5dd5000+b2e000]
Dec  1 08:38:51 Thor kernel: [22128.008411] /usr/bin/deluge[3737]: segfault at c1 ip 0000000000439cc3 sp 00007fffafa51b68 error 4 in python2.6[400000+21a000]
Dec  1 10:56:32 Thor kernel: [30389.774311] python[3341]: segfault at 20 ip 00007f5f71603344 sp 00007fff3da676e0 error 6 in libc-2.12.1.so[7f5f7159a000+17a000]
Dec  1 11:04:11 Thor kernel: [30848.885180] python[5036]: segfault at 2e2929746928 ip 00002e2929746928 sp 00007fff7a3dee18 error 14 in libnss_files-2.12.1.so[7f6202e43000+c000]
Dec  1 13:36:06 Thor kernel: [39963.719115] python[5909]: segfault at 2e2929746928 ip 00002e2929746928 sp 00007fffcb786128 error 14 in libbz2.so.1.0.4[7fb7a675e000+f000]
Dec  1 21:49:31 Thor kernel: [   21.155578] sh[594]: segfault at 0 ip 00007f6cc74b69d5 sp 00007fff3c2ae578 error 4 in ld-2.12.1.so[7f6cc74a5000+20000]
Dec  1 22:15:37 Thor kernel: [  170.033269] gnome-settings-[1927]: segfault at 0 ip 00007f14894c0a48 sp 00007fff50faf658 error 6 in libc-2.12.1.so[7f14893e9000+17a000]
Dec  1 22:37:28 Thor kernel: [ 1481.187734] chromium-browse[2431]: segfault at b0 ip 00007fcadd24a3ab sp 00007fffbcfd9900 error 4 in chromium-browser[7fcadc1fc000+2e96000]
Dec  2 13:06:45 Thor kernel: [48545.516058] /usr/bin/deluge[5066]: segfault at c1 ip 0000000000439cc3 sp 00007fff4a9cab28 error 4 in python2.6[400000+21a000]
Dec  2 13:34:29 Thor kernel: [  320.272737] update-manager[2188]: segfault at 98 ip 00000000004508b6 sp 00007fff9d1d8870 error 4 in python2.6[400000+21a000]
Dec  2 13:40:59 Thor kernel: [  709.568718] rhythmbox[2340]: segfault at 7ffac8e20a60 ip 00007ffac8e20a60 sp 00007fff420b87e8 error 15 in libpython2.6.so.1.0[7ffac8e09000+62000]
Dec  2 16:39:39 Thor kernel: [ 9612.835519] chromium-browse[3094]: segfault at 7f8c1aacc7c8 ip 00007f8eae3a2076 sp 00007fffec85b490 error 4 in chromium-browser[7f8ead55b000+2e96000]
Dec  2 18:21:37 Thor kernel: [15730.921314] chromium-browse[3969]: segfault at 6342 ip 00007f8eae39cef6 sp 00007fffec85b3c0 error 4 in chromium-browser[7f8ead55b000+2e96000]
Dec  3 01:58:39 Thor kernel: [ 2578.696808] update-manager[3222]: segfault at 0 ip (null) sp 00007fff9980b4f8 error 14 in python2.6[400000+21a000]
Dec  3 10:45:46 Thor kernel: [34206.281078] /usr/bin/deluge[5736]: segfault at 0 ip (null) sp 00007fffc7711058 error 14 in python2.6[400000+21a000]
Dec  3 11:16:30 Thor kernel: [36050.004479] npviewer.bin[6021]: segfault at f577d04c ip 00000000f618bee7 sp 00000000fff6c360 error 4 in libflashplayer.so[f5dec000+b2e000]
Dec  3 11:21:40 Thor kernel: [36359.971880] update-manager[6162]: segfault at 0 ip (null) sp 00007fff8377be08 error 14 in python2.6[400000+21a000]
Dec  3 11:57:30 Thor kernel: [38509.834865] chromium-browse[5921]: segfault at 0 ip 00007f1393e1fced sp 00007fff4a9b0500 error 4 in libgtk-x11-2.0.so.0.2200.0[7f1393bce000+412000]
Dec  3 12:04:41 Thor kernel: [38941.225046] python[7124]: segfault at 0 ip (null) sp 00007f06590767e8 error 14 in python2.6[400000+21a000]

```

As you can see its not related to one program. I looked in the BIOS to see if anything was off and found nothing. The voltage is running at stock and no overclocking or anything like that. I got this processor from a friend and it was working in his system perfectly. I have 10.10 x64 installed. Let me know if any other logs are needed to help the problem. Thanks!

---

### Post by dcstar on 2010-12-04
> **TaterSalad22 said:**
> Hi All,

I upgraded my processor two days ago(p4 -> C2D), and ever since then I have been getting segfaults, which are causing my programs to crash randomly.
..........
As you can see its not related to one program. I looked in the BIOS to see if anything was off and found nothing. The voltage is running at stock and no overclocking or anything like that. I got this processor from a friend and it was working in his system perfectly. I have 10.10 x64 installed. Let me know if any other logs are needed to help the problem. Thanks!

It is almost 100% certain that you have a hardware problem, so all the logs in the world are going to be no use whatsoever.

Unless the BIOS on your system is **guaranteed** to work with the new CPU **and** you did not damage it with a static charge while handling it **and** the heatsink is working correctly etc. then you may have a flaky system.

---

### Post by efflandt on 2010-12-04
Can you run memtest86+ for hours without errors?

I have experienced a couple of cases of RAM that should have been compatible, that was not quite (RAM that worked fine in another PC).  But that could also be some other hardware or BIOS issue if that cpu was not around when the mobo was made.

I would not worry about npviewer.bin crashes.  I have seen that commonly happen when using flashplugin-installer on 64-bit systems (32-bit flash with npwrapper) and not even noticing when that happens.  That is something I think to protect Firefox from flash crashes.  Real 64-bit flash resolves that, as long as you are running 64-bit and your cpu has the lahf_lm instruction (in output of **cat /proc/cpuinfo**).

---

