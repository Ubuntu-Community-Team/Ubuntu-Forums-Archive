---
title: "skype video segmentation fault"
date: 2009-12-05
forum: General Help
---

### Post by jwaclawsky on 2009-12-05
I tried posting this on the "Dell Support" and  "multimedia & video" but I am not getting any "support" maybe someone can help me here. This looks like some system default has changed as a result of an update. My thoughts are that skype is outputting to X11 or something else and I need to configure the system to use X11 with Skype but I can't find out where to set the system default to X11 for all my video, or should I be using something else? My detailed problem is:

Skype was working fine on my Dell Mini 9 with Ubuntu 9.04 and then I installed the updates from the update manager yesterday (which I noticed included some skype updates) and then after that Skype crashes when I start my video. I thought there might be a problem in the update so I waited to see if a new update happens, and today I installed another set of updates hoping that would solve the problem (but I didn't notice any skype updates in it). I am not sure if the problem was due to the updates but I hadn't done anything else and that is the only skype change that I am aware of. I still have the problem.

I have ran a test to my wife's windows XP machine (which always worked before). Another symptom is there is a very long delay in the voice from my computer (over 3 seconds of delay) to her XP machine but no delay from my wife's computer back to mine (we can hear each other speaking in the different rooms of my house so we can time the delay). Then when she starts her video or when I test skype video in the skype options menu the result is a repeating error.

X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)
X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)
X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)
....etc.....

However, when I start my video on a call the repeating error stops and the skype crashes with a "segment fault" error message

.
.
.
X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)
Segmentation fault

Can anyone tell me where I can find information on this error and error code. I would be grateful for any assistance. Thanks

---

### Post by jwaclawsky on 2009-12-06
Bump ...can anyone give me an idea of what is wrong or where to get assistance. Many thanks.

---

### Post by jwaclawsky on 2009-12-07
Am I doing something wrong????  Everyone is ignoring me  :-( 

I have been doing some more debugging and ran the following command
sudo gstreamer-properties then I selected the Video tab and tested the default input (The plug-in was "Video for Linux 2 (v4|2)".   I received the following output when I clicked on test:

The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 68 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.) 

When I did it a second time (and subsequent times after that) I got the following error:

The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 61 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I ran a test and received the following repeating messages then the failure when I turned on video: 

X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation) 
X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation) 
*** glibc detected *** /usr/bin/skype.real: double free or corruption (!prev): 0x0a4aa418 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6e30604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb6e325b6]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7013231]
/usr/lib/libstdc++.so.6(_ZdaPv+0x1d)[0xb701328d]
/usr/bin/skype.real[0x892903f]
/usr/bin/skype.real[0x89301b5]
/usr/bin/skype.real[0x893099e]
/usr/bin/skype.real[0x8905c78]
/usr/bin/skype.real[0x89b49b5]
/usr/bin/skype.real[0x88f0092]
/lib/tls/i686/cmov/libpthread.so.0[0xb704f4ff]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb6ea549e]
======= Memory map: ========
08048000-0922f000 rwxp 00000000 08:01 458795     /usr/bin/skype.real
0922f000-09268000 rwxp 0922f000 00:00 0 
0946b000-0a813000 rwxp 0946b000 00:00 0          [heap]
9c633000-9c634000 ---p 9c633000 00:00 0 
9c634000-9ce34000 rwxp 9c634000 00:00 0 
a0e35000-a0e5b000 rwxs 00072000 00:0f 4752       /dev/video0
a0e5b000-a0e81000 rwxs 0004c000 00:0f 4752       /dev/video0
a0e81000-a0ea7000 rwxs 00026000 00:0f 4752       /dev/video0
a0ea7000-a0ecd000 rwxs 00000000 00:0f 4752       /dev/video0
a0ecd000-a4ecd000 rwxp a0ecd000 00:00 0 
a4ecd000-a4ece000 ---p a4ecd000 00:00 0 
a4ece000-a56ce000 rwxp a4ece000 00:00 0 
a7500000-a75fd000 rwxp a7500000 00:00 0 
a75fd000-a7600000 ---p a75fd000 00:00 0 
a76cb000-a76cc000 ---p a76cb000 00:00 0 
a76cc000-a7ecc000 rwxp a76cc000 00:00 0 
a7ecc000-a7ecd000 ---p a7ecc000 00:00 0 
a7ecd000-a86cd000 rwxp a7ecd000 00:00 0 
a86cd000-a86ce000 ---p a86cd000 00:00 0 
a86ce000-a8ece000 rwxp a86ce000 00:00 0 
a8ece000-a8ecf000 ---p a8ece000 00:00 0 
a8ecf000-a9ad0000 rwxp a8ecf000 00:00 0 
a9ad0000-a9ad1000 ---p a9ad0000 00:00 0 
a9ad1000-aa2d1000 rwxp a9ad1000 00:00 0 
aa2d1000-aa2d2000 ---p aa2d1000 00:00 0 
aa2d2000-aaad2000 rwxp aa2d2000 00:00 0 
aaad2000-abee7000 r-xp 00000000 08:01 804481     /usr/share/fonts/truetype/arphic/uming.ttc
abee7000-ad2fc000 r-xp 00000000 08:01 804481     /usr/share/fonts/truetype/arphic/uming.ttc
ad2fc000-b12fd000 rwxs 00000000 00:15 71019      /dev/shm/pulse-shm-1965922582
b12fd000-b12fe000 ---p b12fd000 00:00 0 
b12fe000-b1afe000 rwxp b12fe000 00:00 0 
b1b27000-b20ef000 rwxp b1b27000 00:00 0 
b20ef000-b2b00000 r-xp 00000000 08:01 804496     /usr/share/fonts/truetype/sazanami/sazanami-mincho.ttf
b2b00000-b2bef000 rwxp b2b00000 00:00 0 
b2bef000-b2c00000 ---p b2bef000 00:00 0 
b2cb6000-b2cb7000 ---p b2cb6000 00:00 0 
b2cb7000-b34b7000 rwxp b2cb7000 00:00 0 
b3581000-b3594000 r-xp 00000000 08:01 804610     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_hi.ttf
b3594000-b35a8000 r-xp 00000000 08:01 804609     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_gu.ttf
b35a8000-b35ca000 r-xp 00000000 08:01 1090064    /usr/share/fonts/truetype/ttf-bengali-fonts/lohit_bn.ttf
b35ca000-b37e6000 r-xp 00000000 08:01 804617     /usr/share/fonts/truetype/unfonts/UnDotum.ttf
b37e6000-b3f3c000 r-xp 00000000 08:01 804495     /usr/share/fonts/truetype/sazanami/sazanami-gothic.ttf
b4100000-b41f2000 rwxp b4100000 00:00 0 
b41f2000-b4200000 ---p b41f2000 00:00 0 
b428e000-b4300000 r-xp 00000000 08:01 804486     /usr/share/fonts/truetype/freefont/FreeSans.ttf
b4300000-b4317000 r-xp 00000000 08:01 1090082    /usr/share/fonts/truetype/ttf-oriya-fonts/lohit_or.ttf
b4317000-b433d000 r-xp 00000000 08:01 1090088    /usr/share/fonts/truetype/ttf-telugu-fonts/lohit_te.ttf
b433d000-b433e000 rwxp b433d000 00:00 0 
b433e000-b433f000 ---p b433e000 00:00 0 
b433f000-b43bf000 rwxp b433f000 00:00 0 
b43d5000-b4403000 r-xp 00000000 08:01 1090074    /usr/share/fonts/truetype/ttf-kannada-fonts/lohit_kn.ttf
b4403000-b4431000 r-xp 00000000 08:01 804605     /usr/share/fonts/truetype/ttf-indic-fonts-core/MuktiNarrow.ttf
b4431000-b4445000 r-xp 00000000 08:01 804547     /usr/share/fonts/truetype/thai/Waree.ttf
b4445000-b4489000 r-xp 00000000 08:01 1540180    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b4489000-b44ac000 r-xp 00000000 08:01 1540196    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b44ac000-b44fd000 r-xp 00000000 08:01 802885     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-ExtraLight.ttf
b44fd000-b4630000 r-xp 00000000 08:01 598073     /lib/i686/cmov/libcrypto.so.0.9.8
b4630000-b4638000 r-xp 00132000 08:01 598073     /lib/i686/cmov/libcrypto.so.0.9.8
b4638000-b4645000 rwxp 0013a000 08:01 598073     /lib/i686/cmov/libcrypto.so.0.9.8
b4645000-b4649000 rwxp b4645000 00:00 0 
b4649000-b468b000 r-xp 00000000 08:01 598092     /lib/i686/cmov/libssl.so.0.9.8
b468b000-b468c000 ---p 00042000 08:01 598092     /lib/i686/cmov/libssl.so.0.9.8
b468c000-b468d000 r-xp 00042000 08:01 598092     /lib/i686/cmov/libssl.so.0.9.8
b468d000-b4690000 rwxp 00043000 08:01 598092     /lib/i686/cmov/libssl.so.0.9.8
b4690000-b46ed000 r-xp 00000000 08:01 688795     /usr/lib/libpulse.so.0.7.1
b46ed000-b46ee000 r-xp 0005c000 08:01 688795     /usr/lib/libpulse.so.0.7.1
b46ee000-b46ef000 rwxp 0005d000 08:01 688795     /usr/lib/libpulse.so.0.7.1
b46f0000-b4700000 r-xp 00000000 08:01 804612     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_ta.ttf
b4700000-b47ff000 rwxp b4700000 00:00 0 
b47ff000-b4800000 ---p b47ff000 00:00 0 
b480f000-b4823000 r-xp 00000000 08:01 811051     /usr/share/fonts/type1/gsfonts/n019003l.pfb
b4823000-b4828000 r-xp 00000000 08:01 615711     /lib/tls/i686/cmov/libnss_dns-2.9.so
b4828000-b4829000 r-xp 00004000 08:01 615711     /lib/tls/i686/cmov/libnss_dns-2.9.so
b4829000-b482a000 rwxp 00005000 08:01 615711     /lib/tls/i686/cmov/libnss_dns-2.9.so
b482a000-b483b000 r-xp 00000000 08:01 599344     /lib/libresolv-2.9.so
b483b000-b483c000 r-xp 00010000 08:01 599344     /lib/libresolv-2.9.so
b483c000-b483d000 rwxp 00011000 08:01 599344     /lib/libresolv-2.9.so
b483d000-b483f000 rwxp b483d000 00:00 0 
b484a000-b4850000 r-xp 00000000 08:01 804611     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_pa.ttf
b4850000-b4854000 r-xp 00000000 08:01 598051     /lib/libattr.so.1.1.0
b4854000-b4855000 r-xp 00003000 08:01 598051     /lib/libattr.so.1.1.0
b4855000-b4856000 rwxp 00004000 08:01 598051     /lib/libattr.so.1.1.0
b4856000-b4857000 ---p b4856000 00:00 0 
b4857000-b48d7000 rwxp b4857000 00:00 0 
b48d7000-b48d8000 ---p b48d7000 00:00 0 
b48d8000-b4958000 rwxp b48d8000 00:00 0 
b4958000-b4959000 ---p b4958000 00:00 0 
b4959000-b5159000 rwxp b4959000 00:00 0 
b5159000-b515a000 ---p b5159000 00:00 0 
b515a000-b595a000 rwxp b515a000 00:00 0 
b595a000-b595b000 ---p b595a000 00:00 0 
b595b000-b59db000 rwxp b595b000 00:00 0 
b59db000-b59dc000 ---p b59db000 00:00 0 
b59dc000-b5a5c000 rwxp b59dc000 00:00 0 
b5a5c000-b5a5d000 ---p b5a5c000 00:00 0 
b5a5d000-b5add000 rwxp b5a5d000 00:00 0 
b5add000-b5b69000 r-xp 00000000 08:01 804597     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5b69000-b5c01000 r-xp 00000000 08:01 804598     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5c01000-b5c53000 r-xp 00000000 08:01 689347     /usr/lib/libtiff.so.4.2.1
b5c53000-b5c54000 ---p 00052000 08:01 689347     /usr/lib/libtiff.so.4.2.1
b5c54000-b5c56000 r-xp 00052000 08:01 689347     /usr/lib/libtiff.so.4.2.1
b5c56000-b5c57000 rwxp 00054000 08:01 689347     /usr/lib/libtiff.so.4.2.1
b5c57000-b5ca9000 r-xp 00000000 08:01 689691     /usr/lib/libQtSvg.so.4.5.0
b5ca9000-b5caa000 ---p 00052000 08:01 689691     /usr/lib/libQtSvg.so.4.5.0
b5caa000-b5cab000 r-xp 00052000 08:01 689691     /usr/lib/libQtSvg.so.4.5.0
b5cab000-b5cac000 rwxp 00053000 08:01 689691     /usr/lib/libQtSvg.so.4.5.0
b5cac000-b5cdc000 r-xp 00000000 08:01 483955     /usr/lib/liblcms.so.1.0.18
b5cdc000-b5cdd000 r-xp 00030000 08:01 483955     /usr/lib/liblcms.so.1.0.18
b5cdd000-b5cde000 rwxp 00031000 08:01 483955     /usr/lib/liblcms.so.1.0.18
b5cde000-b5ce0000 rwxp b5cde000 00:00 0 
b5ce0000-b5d4b000 r-xp 00000000 08:01 483988     /usr/lib/libmng.so.1.1.0.9
b5d4b000-b5d4e000 rwxp 0006a000 08:01 483988     /usr/lib/libmng.so.1.1.0.9
b5d53000-b5d58000 r-xp 00000000 08:01 483650     /usr/lib/libgdbm.so.3.0.0
b5d58000-b5d59000 r-xp 00004000 08:01 483650     /usr/lib/libgdbm.so.3.0.0
b5d59000-b5d5a000 rwxp 00005000 08:01 483650     /usr/lib/libgdbm.so.3.0.0
b5d5a000-b5d5d000 r-xp 00000000 08:01 598062     /lib/libcap.so.2.11
b5d5d000-b5d5e000 r-xp 00002000 08:01 598062     /lib/libcap.so.2.11
b5d5e000-b5d5f000 rwxp 00003000 08:01 598062     /lib/libcap.so.2.11
b5d5f000-b5d7e000 r-xp 00000000 08:01 483939     /usr/lib/libjpeg.so.62.0.0
b5d7e000-b5d7f000 rwxp 0001e000 08:01 483939     /usr/lib/libjpeg.so.62.0.0
b5d7f000-b5d80000 rwxp b5d7f000 00:00 0 
b5d80000-b5d82000 r-xp 00000000 08:01 598111     /lib/libnss_mdns4_minimal.so.2
b5d82000-b5d83000 rwxp 00001000 08:01 598111     /lib/libnss_mdns4_minimal.so.2
b5d83000-b5d87000 r-xp 00000000 08:01 737335     /usr/lib/qt4/plugins/imageformats/libqSegmentation fault

---

### Post by jwaclawsky on 2009-12-07
Bump ....help anyone, please???

---

### Post by Slade Winstone on 2009-12-12
Firstly, I'm not sure if this will help at all (YMMV), but here goes:

Specs:
- Running Jaunty 9.04
- Intel Graphics (laptop screen supports up to 1280x800)
- Skype 2.1 Beta (direct from the skype) for i386
- USB Logitech QuickCam Communicate STX webcam (gspca driver?)

FIRST PROBLEM:
==============

Apparently V4L (video drivers) have switched from version 1 to 2, or something like that, for that webcam chipset and you have to point them back to the older drivers to get Skype to work with the command:

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

This command will load Skype with the appropriate V4L older compatibility drivers (ver 1).

SECOND PROBLEM:
===============

Now, when I ran up Skype in a terminal and tried to test the Video I got the error message:

"X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)"

This is actually an indication of a problem with video playback/the intel video drivers.

What I found was the for some strange reason the xorg.conf had some bad virtual display sizing (didn't put it there, and I would like to know what did!).

So, in /etc/X11/xorg.conf, the Screen Section had bad Virtual sizing:

<<BAD ENTRY>>

Section "Screen"
  SubSection "Display"
    Virtual 2304 800
  EndSubSection
EndSection

<<CORRECTED ENTRY>>

Section "Screen"
  SubSection "Display"
    Virtual 1280 800
  EndSubSection
EndSection

This corrected my problems and I can Skype with video now.

If you are still experiencing problems, try looking at your Intel graphics driver.

Hope that this helps you/somebody.

Slade.

---

