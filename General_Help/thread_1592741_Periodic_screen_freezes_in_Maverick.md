---
title: "Periodic screen freezes in Maverick"
date: 2010-10-10
forum: General Help
---

### Post by spoon_ on 2010-10-10
Fresh install of Ubuntu 10.10.

Every 15 minutes or so, the screen freezes for a few seconds. I can still move the mouse, but everything else is unresponsive. After it unfreezes, I can see that during the freeze CPU utilization was at 100% (on the system monitor applet).

My system:
Ubuntu 10.10 64-bit
Intel Core 2 Duo E6600
Nvidia GTX 280, using drivers downloaded from nvidia.com
Compiz enabled

No such problem existed in Lucid 64-bit. Anyone have any idea what I can do?

I believe [this]("http://ubuntuforums.org/showthread.php?t=1572412") thread is reporting the same problem, but that forum is now locked.

Thanks.

---

### Post by gordintoronto on 2010-10-11
Why would you download a driver instead of installing through Additional Drivers? 

If you run Accessories/Terminal and enter the command: 
top
it will show you what is eating the CPU. Or CPUs, as the case may be.

---

### Post by spoon_ on 2010-10-11
Just habit to grab the latest driver from nvidia. In the past the drivers provided by ubuntu were out of date. I'm using the ubuntu-provided drivers now and experiencing the same problem. And top doesn't tell you what WAS eating the CPUs at the time of the freeze. I wrote a script to periodically run ps and find that out. So next time it happens, hopefully I'll know.

---

### Post by spoon_ on 2010-10-11
I should add also that only one of the cores is utilized during the freeze. I'm pretty sure that the cpu usage is a symptom of the problem, not the cause. One core going to 100% should not cause a dual-core machine to hang.

---

### Post by spoon_ on 2010-10-11
No cpu usage spike recorded by ps aux during the last few 12-second freezes. Sound keeps playing, things appear to be executing normally (ps aux sure is), but the screen freezes. After it all, the system monitor applet thinks that cpu usage was high for the duration of the freeze, but I'm not sure why there's a discrepancy between that and what ps aux says. Is ps aux ignoring some processes (system ones maybe?) that the system monitor applet isn't?

---

### Post by hkphooey on 2010-10-11
I've been getting these as well, and can't figure out what is causing them. I'm guessing its a display driver issue as it normally happens when I click something with the mouse. However in my case the computer never recovers - I have to do a hard reboot. CTRL ALT DELETE / BACKSPACE and Alt-F2 don't do anything. 

The reason I'm mentioning this is in case my troubleshooting method is useful to you. I run an ssh server on the afflicted machine. When the display freezes, I can still login by ssh and investigate what's going on there.

---

### Post by spoon_ on 2010-10-12
Wow these freezes have become insanely annoying now. They seem to intensify when the system is under load, to the point that they're happening about once a minute now. Also sometimes I can't even move my mouse during the freeze. According to top, Xorg consumes 100% of the CPU after returning from the freeze.

---

### Post by spoon_ on 2010-10-13
whoops, double post

---

### Post by spoon_ on 2010-10-13
Hahahah now it just got itself into a freezing loop, where the time between freezes was some tiny fraction of a second. Only way out was to push reset. 

Also the problem exists whether compiz is enabled or not.

---

### Post by spoon_ on 2010-10-13
Ooh here's something from /var/logs/Xorg.0.log

```
Backtrace:
[   521.283] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[   521.283] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a0824]
[   521.283] 2: /usr/bin/X (xf86PostMotionEventP+0xc4) [0x47c194]
[   521.283] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7fb318fd6000+0x5399) [0x7fb318fdb399]
[   521.283] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7fb318fd6000+0x5a8e) [0x7fb318fdba8e]
[   521.283] 5: /usr/bin/X (0x400000+0x6b837) [0x46b837]
[   521.283] 6: /usr/bin/X (0x400000+0x11f4e3) [0x51f4e3]
[   521.283] 7: /lib/libpthread.so.0 (0x7fb31f100000+0xfb40) [0x7fb31f10fb40]
[   521.283] 8: (vdso) (0x7fffde369000+0x70a) [0x7fffde36970a]
[   521.283] 9: (vdso) (__vdso_gettimeofday+0x2d) [0x7fffde3697bd]
[   521.283] 10: /lib/libc.so.6 (__gettimeofday+0x1a) [0x7fb31e0e6c9a]
[   521.283] 11: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fb319a78000+0x6c1c5) [0x7fb319ae41c5]
[   521.283] 12: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fb319a78000+0xca316) [0x7fb319b42316]
[   521.283] 13: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fb319a78000+0x976b2) [0x7fb319b0f6b2]
[   521.283] 14: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fb319a78000+0x3b622d) [0x7fb319e2e22d]
[   521.283] 15: /usr/bin/X (0x400000+0x16a27c) [0x56a27c]
[   521.283] 16: /usr/bin/X (0x400000+0xa352c) [0x4a352c]
[   521.283] 17: /usr/bin/X (BlockHandler+0x50) [0x431480]
[   521.283] 18: /usr/bin/X (WaitForSomething+0x141) [0x45b361]
[   521.283] 19: /usr/bin/X (0x400000+0x2bfd2) [0x42bfd2]
[   521.283] 20: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[   521.283] 21: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fb31e06bd8e]
[   521.283] 22: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[   522.582] (WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00001e8c, 0x00001e8c)
[   523.983] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[   523.983] 

```

That infinite loop bit appears in there a whole lot. This seems to support the idea that I'm experiencing the bug reported here: [https://bugs.freedesktop.org/show_bug.cgi?id=30032]("https://bugs.freedesktop.org/show_bug.cgi?id=30032")

---

### Post by josephdunn on 2010-10-13
I installed Maverick yesterday (was running Lucid previously) on my amd64 system and now I'm experiencing this problem as well. Can't run the nVidia binary drivers since they cause [this]("https://bugs.launchpad.net/bugs/649809") bug, so I was using Nouveau and experienced two lock-ups today. Incidentally, I had experienced one yesterday with the install CD booted, but wrote it off as a glitch.

Anyway, the second time the system locked up I ssh'ed in from my wife's netbook and was able to see that the Xorg process was steadily eating more and more CPU. Neither a kill nor a kill -9 affected it. Eventually the SSH session quit responding. The only way for me to fix this when it happens is to do an Alt+SysReq+REISUB to reboot the machine, but none of the letters except the last seem to have any effect, and the machine comes back up with the partition dirty.

I've solved this for the moment by switching to the old "nv" driver. This is the third Maverick bug that's bit me since I installed yesterday. I love Ubuntu and don't want to be critical, but it feels like they didn't test this release much.

Here are the relevant lines from my /var/log/Xorg.0.log:

[  3054.747] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  8988.035] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[  8988.035]
Backtrace:
[  8988.036] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[  8988.036] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a0824]
[  8988.036] 2: /usr/bin/X (xf86PostButtonEventP+0xcf) [0x47bdaf]
[  8988.036] 3: /usr/bin/X (xf86PostButtonEvent+0xb9) [0x47bed9]
[  8988.036] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7fb8e5d5c000+0x5424) [0x7fb8e5d61424]
[  8988.036] 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x7fb8e5d5c000+0x5a8e) [0x7fb8e5d61a8e]
[  8988.036] 6: /usr/bin/X (0x400000+0x6b837) [0x46b837]
[  8988.036] 7: /usr/bin/X (0x400000+0x11f4e3) [0x51f4e3]
[  8988.036] 8: /lib/libpthread.so.0 (0x7fb8eb5a8000+0xfb40) [0x7fb8eb5b7b40]
[  8988.036] 9: /lib/libc.so.6 (ioctl+0x7) [0x7fb8ea5d3447]
[  8988.036] 10: /lib/libdrm.so.2 (drmIoctl+0x28) [0x7fb8e8b820a8]
[  8988.036] 11: /lib/libdrm.so.2 (drmCommandWrite+0x1b) [0x7fb8e8b8232b]
[  8988.036] 12: /lib/libdrm_nouveau.so.1 (0x7fb8e8544000+0x2a9d) [0x7fb8e8546a9d]
[  8988.036] 13: /lib/libdrm_nouveau.so.1 (nouveau_bo_map_range+0xff) [0x7fb8e8546c8f]
[  8988.036] 14: /lib/libdrm_nouveau.so.1 (0x7fb8e8544000+0x1d1a) [0x7fb8e8545d1a]
[  8988.036] 15: /lib/libdrm_nouveau.so.1 (nouveau_pushbuf_flush+0x190) [0x7fb8e85460f0]
[  8988.036] 16: /usr/lib/xorg/modules/libexa.so (0x7fb8e769c000+0x9c95) [0x7fb8e76a5c95]
[  8988.036] 17: /usr/lib/xorg/modules/libexa.so (0x7fb8e769c000+0xaee1) [0x7fb8e76a6ee1]
[  8988.036] 18: /usr/bin/X (0x400000+0xd8dbd) [0x4d8dbd]
[  8988.036] 19: /usr/lib/xorg/modules/libexa.so (0x7fb8e769c000+0xd230) [0x7fb8e76a9230]
[  8988.036] 20: /usr/bin/X (0x400000+0xd8590) [0x4d8590]
[  8988.036] 21: /usr/bin/X (0x400000+0xd2378) [0x4d2378]
[  8988.036] 22: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
[  8988.036] 23: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[  8988.036] 24: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fb8ea513d8e]
[  8988.036] 25: /usr/bin/X (0x400000+0x213d9) [0x4213d9]

---

### Post by spoon_ on 2010-10-13
Yeah it looks like it's an Xorg bug that can manifest itself no matter what driver we use.

---

### Post by mochuk on 2010-10-13
I also have the same sporadically freezes of graphics and cursor.

If I view flash videos, also the video stops sporadically: First the sound stops, then a little bit later, the video stops. After a short time the sound starts again and afterwards the video starts.

Im Using Ubuntu 10.10 64bit on a laptop HP 6910p with an ATI Mobility X2300 graphics card. Driver used is radeon.

Maybe this information helps to find the problem.

---

### Post by petrasflorin on 2010-10-13
Check this [http://ubuntuforums.org/showthread.php?t=1595989](http://ubuntuforums.org/showthread.php?t=1595989)

and this [http://ubuntuforums.org/showthread.php?t=1592108](http://ubuntuforums.org/showthread.php?t=1592108)

---

### Post by spoon_ on 2010-10-13
> **petrasflorin said:**
> Check this [http://ubuntuforums.org/showthread.php?t=1595989](http://ubuntuforums.org/showthread.php?t=1595989)

and this [http://ubuntuforums.org/showthread.php?t=1592108](http://ubuntuforums.org/showthread.php?t=1592108)

Have you confirmed that you're actually experiencing the same Xorg-related issue that we are? I suspect your problem is different, but thanks for the tip.

---

### Post by spoon_ on 2010-10-13
> **mochuk said:**
> I also have the same sporadically freezes of graphics and cursor.

If I view flash videos, also the video stops sporadically: First the sound stops, then a little bit later, the video stops. After a short time the sound starts again and afterwards the video starts.

Im Using Ubuntu 10.10 64bit on a laptop HP 6910p with an ATI Mobility X2300 graphics card. Driver used is radeon.

Maybe this information helps to find the problem.

This is somewhat different from what I've experienced because my sound never stops. All processes (including sound-emitting ones) continue functioning normally during the freeze. In my case, the freeze is purely visual, and it affects the entire screen at once -- not just a video.

---

### Post by mochuk on 2010-10-14
> **spoon_ said:**
> This is somewhat different from what I've experienced because my sound never stops. All processes (including sound-emitting ones) continue functioning normally during the freeze. In my case, the freeze is purely visual, and it affects the entire screen at once -- not just a video.

Beside the freeze problem of the flash video I also get freezes of the screen during normal work. The freezes only affect my cursor, but not the gif animations in the browser.

Additionally to these "normal" freezes - if I watch flash videos - the only sound that stops is the sound of the flash video. It seems not to be related to the hanging of the sound process, but more related to resynchronizing the audio with the gapped video stream. Unfortunately I'm not able to reproduce the flash freezes right now to check, whether the sound or the video ist the first one that stops.

---

### Post by spoon_ on 2010-10-15
> **josephdunn said:**
> I installed Maverick yesterday (was running Lucid previously) on my amd64 system and now I'm experiencing this problem as well. Can't run the nVidia binary drivers since they cause [this]("https://bugs.launchpad.net/bugs/649809") bug, so I was using Nouveau and experienced two lock-ups today. Incidentally, I had experienced one yesterday with the install CD booted, but wrote it off as a glitch.

Anyway, the second time the system locked up I ssh'ed in from my wife's netbook and was able to see that the Xorg process was steadily eating more and more CPU. Neither a kill nor a kill -9 affected it. Eventually the SSH session quit responding. The only way for me to fix this when it happens is to do an Alt+SysReq+REISUB to reboot the machine, but none of the letters except the last seem to have any effect, and the machine comes back up with the partition dirty.

I've solved this for the moment by switching to the old "nv" driver. This is the third Maverick bug that's bit me since I installed yesterday. I love Ubuntu and don't want to be critical, but it feels like they didn't test this release much.

Here are the relevant lines from my /var/log/Xorg.0.log:

[  3054.747] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  8988.035] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[  8988.035]
Backtrace:
[  8988.036] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[  8988.036] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a0824]
[  8988.036] 2: /usr/bin/X (xf86PostButtonEventP+0xcf) [0x47bdaf]
[  8988.036] 3: /usr/bin/X (xf86PostButtonEvent+0xb9) [0x47bed9]
[  8988.036] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7fb8e5d5c000+0x5424) [0x7fb8e5d61424]
[  8988.036] 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x7fb8e5d5c000+0x5a8e) [0x7fb8e5d61a8e]
[  8988.036] 6: /usr/bin/X (0x400000+0x6b837) [0x46b837]
[  8988.036] 7: /usr/bin/X (0x400000+0x11f4e3) [0x51f4e3]
[  8988.036] 8: /lib/libpthread.so.0 (0x7fb8eb5a8000+0xfb40) [0x7fb8eb5b7b40]
[  8988.036] 9: /lib/libc.so.6 (ioctl+0x7) [0x7fb8ea5d3447]
[  8988.036] 10: /lib/libdrm.so.2 (drmIoctl+0x28) [0x7fb8e8b820a8]
[  8988.036] 11: /lib/libdrm.so.2 (drmCommandWrite+0x1b) [0x7fb8e8b8232b]
[  8988.036] 12: /lib/libdrm_nouveau.so.1 (0x7fb8e8544000+0x2a9d) [0x7fb8e8546a9d]
[  8988.036] 13: /lib/libdrm_nouveau.so.1 (nouveau_bo_map_range+0xff) [0x7fb8e8546c8f]
[  8988.036] 14: /lib/libdrm_nouveau.so.1 (0x7fb8e8544000+0x1d1a) [0x7fb8e8545d1a]
[  8988.036] 15: /lib/libdrm_nouveau.so.1 (nouveau_pushbuf_flush+0x190) [0x7fb8e85460f0]
[  8988.036] 16: /usr/lib/xorg/modules/libexa.so (0x7fb8e769c000+0x9c95) [0x7fb8e76a5c95]
[  8988.036] 17: /usr/lib/xorg/modules/libexa.so (0x7fb8e769c000+0xaee1) [0x7fb8e76a6ee1]
[  8988.036] 18: /usr/bin/X (0x400000+0xd8dbd) [0x4d8dbd]
[  8988.036] 19: /usr/lib/xorg/modules/libexa.so (0x7fb8e769c000+0xd230) [0x7fb8e76a9230]
[  8988.036] 20: /usr/bin/X (0x400000+0xd8590) [0x4d8590]
[  8988.036] 21: /usr/bin/X (0x400000+0xd2378) [0x4d2378]
[  8988.036] 22: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
[  8988.036] 23: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[  8988.036] 24: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fb8ea513d8e]
[  8988.036] 25: /usr/bin/X (0x400000+0x213d9) [0x4213d9]

Hey I haven't used the nouveau driver but does it have a way to adjust powermizer settings? When I set powermizer to "maximum performance" in nvidia-settings, my lockups seem to go away. I might end up rescinding this later, but it's been quite a while now, and I haven't experienced one.

EDIT:
Oh look, other people reporting the same thing: [http://www.nvnews.net/vbulletin/showthread.php?t=155342](http://www.nvnews.net/vbulletin/showthread.php?t=155342)

So it  might be powermizer's fault.

---

### Post by rsansores on 2010-10-20
Same problem here ubuntu 10.10 desktop edition amd64.

Im working and at some point everything frezees. I can't even change to other TTY using control + ALT + F1. This is really nasty, normally even in a complete gnome crash I was able to change to other terminal and restart Xs but this bug dont allow to do anything, you need to poweroff the computer. Im not complete sure but like some people explain in this post this seems to be related to nvidia graphics because some times this happends when Im using the desktop cube. Like the first post says if im using rythmbox I can hear the music play even after the freeze and usually when this happends the fans of the laptop start at max power.

I have an Nvidia GeForce GTS 360M using the privative drivers provided by ubuntu.

---

### Post by rsansores on 2010-10-20
Almost forgot, anyone knows if theres an official bug regarding this behaivior in the bug tracking system of ubuntu?

---

### Post by spoon_ on 2010-10-20
If your problem is the same as mine, then it's caused by the PowerMizer settings. I "solved" it, for now, by adding this line to /etc/X11/xorg.conf:

```
    Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x1; PowerMizerDefault=0x1; PowerMizerDefaultAC=0x1"
```

to the "Device" section.

This disables Nvidia's power-saving features. Fine for a desktop, might suck if you're on battery though.

---

### Post by rsansores on 2010-10-21
Jackpot! Tnx _spoon, after this tweak I'm not getting any more freezes and not just that, my laptop is running cooler!. I used 0x3 instead 0x1 as value 'cause my video card is really powerfull and compiz works sweet even in the worse clock speed.

:P

---

### Post by AmanicA on 2010-10-21
If ps doesn't pick up what is using the cpu then I'd assume it must be something in the kernel. I had freezes that was caused by swapping;
and my overheating cpu didn't help either - after cleaning out the fans, things are much better.

---

### Post by patientfox on 2010-11-01
> **spoon_ said:**
> If your problem is the same as mine, then it's caused by the PowerMizer settings. I "solved" it, for now, by adding this line to /etc/X11/xorg.conf:

```
    Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x1; PowerMizerDefault=0x1; PowerMizerDefaultAC=0x1"
```to the "Device" section.

This disables Nvidia's power-saving features. Fine for a desktop, might suck if you're on battery though.

Maverick 32bit user here w/ a 7800 GT... I'm running 260.19.06 and decided to check my nvidia settings to see what my PowerMizer settings were.. and they were already at "Maximum Performance".. I went ahead and added the above item to my Xorg.conf anyways and rebooted.. and just repro'd the same behavior on my machine.. 

Here's the output of Xorg.0.log : 

[   789.657] (WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000f4d8, 0x0000f8dc)
[   795.240] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[   795.240] 
Backtrace:
[   795.240] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
[   795.240] 1: /usr/bin/X (mieqEnqueue+0x1ab) [0x80e7aeb]
[   795.240] 2: /usr/bin/X (xf86PostMotionEventP+0xd2) [0x80c2172]
[   795.240] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x780000+0x4961) [0x784961]
[   795.240] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x780000+0x4a56) [0x784a56]
[   795.240] 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x780000+0x5296) [0x785296]
[   795.240] 6: /usr/bin/X (0x8048000+0x6951f) [0x80b151f]
[   795.241] 7: /usr/bin/X (0x8048000+0x126aee) [0x816eaee]
[   795.241] 8: (vdso) (__kernel_sigreturn+0x0) [0xa1c400]
[   796.656] (WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x0000f4d8, 0x0000f8dc)

anyone else seeing this behavior *after* forcing PowerMizer into Maximum Performance?

---

### Post by patientfox on 2010-11-01
I found a really interesting and illustrative email on the topic of the "EQ Overflowing" problem here: 

[http://marc.info/?l=fedora-devel-list&m=124101535025331&w=2](http://marc.info/?l=fedora-devel-list&m=124101535025331&w=2)

tl;dr -- experiencing a lockup and seeing "EQ Overflowing" in the log isn't a single bug, in and of itself, but a symptom of an issue elsewhere in the X Server. This could be related to exotic input drivers, nvidia driver versions, system load/compositing, powermizer settings, etc etc etc.

So I guess take all of the voodoo-solution stuff with a big grain of salt. I personally am going to take some measures to lessen the load on my GPU and improve circulation/reduce core temp.

---

### Post by johnamberg70 on 2010-11-05
Disabling power-saving features was what did the trick for me; at least for now. Also make sure the refresh rate in compiz matches actual rate.  This was a real issue for me and much thanks to "Spoon".

---

