---
title: "Randomly getting corrupted / scrambled graphics -- sometimes locks up/restarts X"
date: 2010-06-25
forum: General Help
---

### Post by mtjohnson on 2010-06-25
Since upgrading to 10.04 I've been getting corrupted graphics / scrambled graphics randomly, usually it occurs more frequently when I have more applications open, especially graphically intensive ones.

When this happens, it will also (once in awhile) lockup the system for a few seconds, and on fewer occasions will cause X to die and restart.

I've been checking my Xorg logs, and did have a log that had this message in it (just before a segfault error):

[mi] EQ overflowing. The server is probably stuck in an infinite loop.

However, I reinstalled yesterday and lost the log. I did see this in my Xorg.0.log today (a segfault without the previous message):

```
(II) Jun 24 16:11:20 NVIDIA(0): Setting mode
(II) Jun 24 16:11:20 NVIDIA(0):     "CRT-0:nvidia-auto-select@1280x1024+1280+0,CRT-1:nvidia-auto-select@1280x1024+0+0"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb78cf410]
Segmentation fault at address 0x300

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```

I've got an Nvidia card and am using the 'current' nvidia driver from the repository. I'm using the Nvida twinview feature with 2 LCD displays at 1280x1024 (set to 'auto' resolution). My system is a Dell E520 desktop, but I have a coworker using Ubuntu 10.04 also and he's having the same issue while on his IBM laptop.

Any ideas, or is anyone else seeing this happen?

I've included a screenshot of the corrupted graphics I get (the app running is Eclipse).

---

### Post by mtjohnson on 2010-06-25
Just had it lock up again, I was able to switch to a virtual terminal (after waiting a long time), and I got this in the Xorg log:

```
(WW) Jun 25 14:31:13 NVIDIA(0): WAIT (0, 6, 0x8000, 0x000049f8, 0x000049f8)
(WW) Jun 25 14:31:16 NVIDIA(0): WAIT (2, 6, 0x8000, 0x000049f8, 0x000005fc)
(WW) Jun 25 14:31:19 NVIDIA(0): WAIT (0, 6, 0x8000, 0x000005fc, 0x000005fc)
[mi] EQ overflowing. The server is probably stuck in an infinite loop.

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (mieqEnqueue+0x1ab) [0x80e8b6b]
2: /usr/bin/X (xf86PostMotionEventP+0xd2) [0x80c2d02]
3: /usr/lib/xorg/modules/input/evdev_drv.so (0xb4ef1000+0x48a1) [0xb4ef58a1]
4: /usr/lib/xorg/modules/input/evdev_drv.so (0xb4ef1000+0x4b96) [0xb4ef5b96]
5: /usr/bin/X (0x8048000+0x6d5bf) [0x80b55bf]
6: /usr/bin/X (0x8048000+0x122794) [0x816a794]
7: (vdso) (__kernel_sigreturn+0x0) [0xb78d0400]
(WW) Jun 25 14:31:22 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00001e90, 0x00001e90)
(WW) Jun 25 14:31:25 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00001f58, 0x00001f58)
(WW) Jun 25 14:31:28 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00003ea4, 0x00003ea4)
(WW) Jun 25 14:31:31 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00005420, 0x00005420)
(WW) Jun 25 14:31:34 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00009fd0, 0x00009fd0)
(WW) Jun 25 14:31:37 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000aecc, 0x0000aecc)
... lots more of this

```

---

