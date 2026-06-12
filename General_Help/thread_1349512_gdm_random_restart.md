---
title: "gdm random restart"
date: 2009-12-08
forum: General Help
---

### Post by kotkis on 2009-12-08
Hi,

Today something strange happened four times last hour:
GDM restarts without reason. First I thought that this is related to my wine applications but then I just opened Nautilus and Gedit .. and after some random browsing ..bum

Ubuntu 9.10 fully updated, 2.6.31-16-generic  , intel 945 video 

At the end of /var/log/gdm/0.log.1 (suppose this is the previous log - for the crash) I saw this:
```

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133dbb]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c1395]
2: [0x19d400]
3: /usr/lib/xorg/modules/drivers//intel_drv.so [0x392574]
4: /usr/bin/X [0x8181800]
5: /usr/bin/X(ProcPutImage+0x159) [0x808a4c9]
6: /usr/bin/X(Dispatch+0x35f) [0x808d1af]
7: /usr/bin/X(main+0x395) [0x8072515]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x230b56]
9: /usr/bin/X [0x80719c1]
Saw signal 7.  Server aborting.
(II) Logitech USB-PS/2 Optical Mouse: Close
(II) AT Translated Set 2 keyboard: Close
(II) Sleep Button: Close
(II) Video Bus: Close
(II) Power Button: Close
(II) Macintosh mouse button emulation: Close
(II) AIGLX: Suspending AIGLX clients for VT switch
Dropping master 
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 7

```There are no errors at the log - just a few warnings

If someone has idea - please help - this is getting really frustrating

Regards

PS: I've never had this problem and just remembered that there was some updates yesterday - synaptic history shows this:
```

Commit Log for Mon Dec  7 09:13:21 2009


Upgraded the following packages:
gdm (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
libdrm-intel1 (2.4.15+git20091119.b4312b63-0ubuntu0tormod~karmic) to 2.4.16+git20091206.9707733a-0ubuntu0sarvatt~karmic
libdrm-radeon1 (2.4.15+git20091119.b4312b63-0ubuntu0tormod~karmic) to 2.4.16+git20091206.9707733a-0ubuntu0sarvatt~karmic
libdrm2 (2.4.15+git20091119.b4312b63-0ubuntu0tormod~karmic) to 2.4.16+git20091206.9707733a-0ubuntu0sarvatt~karmic
libgl1-mesa-dri (7.7.0~git20091123+mesa-7-7-branch.960464e4-0ubuntu0tormod) to 7.7.0~git20091205+mesa-7-7-branch.bc0532b0-0ubuntu0sarvatt
libgl1-mesa-glx (7.7.0~git20091123+mesa-7-7-branch.960464e4-0ubuntu0tormod) to 7.7.0~git20091205+mesa-7-7-branch.bc0532b0-0ubuntu0sarvatt
libglu1-mesa (7.7.0~git20091123+mesa-7-7-branch.960464e4-0ubuntu0tormod) to 7.7.0~git20091205+mesa-7-7-branch.bc0532b0-0ubuntu0sarvatt
libnautilus-extension1 (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
linux-generic (2.6.31.15.28) to 2.6.31.16.29
linux-headers-generic (2.6.31.15.28) to 2.6.31.16.29
linux-image-generic (2.6.31.15.28) to 2.6.31.16.29
linux-libc-dev (2.6.31-15.50) to 2.6.31-16.52
mesa-utils (7.7.0~git20091123+mesa-7-7-branch.960464e4-0ubuntu0tormod) to 7.7.0~git20091205+mesa-7-7-branch.bc0532b0-0ubuntu0sarvatt
nautilus (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
nautilus-data (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
sreadahead (1.0-5) to 1:0.90.3-2
x11-common (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xbase-clients (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-input-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-video-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-video-ati (1:6.12.99+git20091123.b9eb2380-0ubuntu0tormod~karmic) to 1:6.12.99+git20091201.88a50a30-0ubuntu0tormod~karmic
xserver-xorg-video-intel (2:2.9.0+git20091111.dbb68168-0ubuntu0sarvatt) to 2:2.9.99.901+git20091204.415aab47-0ubuntu0tormod~karmic
xserver-xorg-video-radeon (1:6.12.99+git20091123.b9eb2380-0ubuntu0tormod~karmic) to 1:6.12.99+git20091201.88a50a30-0ubuntu0tormod~karmic

Installed the following packages:
linux-headers-2.6.31-16 (2.6.31-16.52)
linux-headers-2.6.31-16-generic (2.6.31-16.52)
linux-image-2.6.31-16-generic (2.6.31-16.52)
ureadahead (0.90.3-2)

```

So if there is no fix for this crash, can someone tell me how to revert this updates?

---

