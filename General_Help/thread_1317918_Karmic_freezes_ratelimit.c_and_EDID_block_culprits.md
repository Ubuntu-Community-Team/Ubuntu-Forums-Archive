---
title: "Karmic freezes: ratelimit.c and EDID block culprits?"
date: 2009-11-07
forum: General Help
---

### Post by lelamal on 2009-11-07
Hi all! I'm on a Thinkpad R50e, and since I did a fresh install of Karmic, I have been experiencing frequent freezes. I haven't applied any workarounds, and the system is as was out-of-the-box. Most of the times it happens while listening to music. When I listen to music and in the meantime I do some other operation which involves the use of the mouse and the appearance of some graphical output (a drop-down menu, a new window open, an old one maximised from the system tray, etc.). The combination of these two events most of the times results in the music got stuck on two notes repeated for two or three seconds at short distance intervals, then everything gets back to normal. Other times I'm not so lucky, and the sound (most times music, but can just as well be system notifications or whatever) keeps going on forever in a loop, and the only thing to stop it is a cold reboot. Video itself, however, never gave me problems of any sort, that is I've been playing movies and the system never froze. I suspect it must have something to do primarily with the sound system.

In the System Log messages, last entries before the freeze usually report variations of the following:

> Nov  2 12:07:06 ECO pulseaudio[1564]: ratelimit.c: 159 events suppressed
Nov  2 12:27:48 ECO pulseaudio[1564]: ratelimit.c: 149 events suppressed
Nov  2 12:28:23 ECO pulseaudio[1564]: ratelimit.c: 68 events suppressed
Nov  2 13:49:25 ECO pulseaudio[1564]: ratelimit.c: 165 events suppressed
Nov  2 14:16:36 ECO pulseaudio[1564]: ratelimit.c: 158 events suppressed
Nov  2 14:44:56 ECO pulseaudio[1564]: ratelimit.c: 32 events suppressed
Nov  2 14:45:06 ECO pulseaudio[1564]: ratelimit.c: 31 events suppressed
Nov  2 14:58:38 ECO pulseaudio[1564]: ratelimit.c: 35 events suppressed
Nov  2 15:41:22 ECO pulseaudio[1564]: ratelimit.c: 156 events suppressed
Nov  2 15:51:33 ECO pulseaudio[1564]: ratelimit.c: 149 events suppressed
Nov  2 15:54:12 ECO pulseaudio[1564]: ratelimit.c: 141 events suppressed
Nov  2 16:01:17 ECO pulseaudio[1564]: ratelimit.c: 152 events suppressed
Nov  2 16:04:33 ECO pulseaudio[1564]: ratelimit.c: 105 events suppressed
Nov  2 16:07:33 ECO pulseaudio[1564]: ratelimit.c: 76 events suppressed
Nov  2 16:50:53 ECO pulseaudio[1564]: ratelimit.c: 108 events suppressed
Nov  2 17:17:22 ECO pulseaudio[1564]: ratelimit.c: 65 events suppressed
Nov  2 17:39:09 ECO pulseaudio[1564]: ratelimit.c: 143 events suppressed
Nov  2 17:48:51 ECO pulseaudio[1564]: ratelimit.c: 161 events suppressed
Nov  2 18:16:49 ECO pulseaudio[1564]: ratelimit.c: 137 events suppressed
Nov  2 18:43:58 ECO pulseaudio[1564]: ratelimit.c: 129 events suppressed
Nov  2 18:47:36 ECO pulseaudio[1564]: ratelimit.c: 155 events suppressed
Nov  2 19:35:40 ECO pulseaudio[1564]: ratelimit.c: 173 events suppressed
Nov  2 19:37:20 ECO pulseaudio[1564]: ratelimit.c: 88 events suppressed
Nov  2 19:39:23 ECO pulseaudio[1564]: ratelimit.c: 66 events suppressed
Nov  2 20:09:16 ECO pulseaudio[1564]: ratelimit.c: 159 events suppressed
Nov  2 22:52:33 ECO pulseaudio[1564]: ratelimit.c: 81 events suppressed
Nov  3 00:33:33 ECO pulseaudio[1564]: ratelimit.c: 62 events suppressed
Nov  3 00:39:26 ECO pulseaudio[1564]: ratelimit.c: 76 events suppressed
Nov  3 02:17:41 ECO pulseaudio[1564]: ratelimit.c: 161 events suppressed
Nov  3 02:47:30 ECO pulseaudio[1564]: ratelimit.c: 153 events suppressed
Nov  3 02:49:19 ECO kernel: [59669.083978] [drm] LVDS-8: set mode 1024x768 d
Nov  3 02:49:21 ECO kernel: [59671.086380] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:22 ECO kernel: [59671.576399] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:22 ECO kernel: [59672.002693] i2c-adapter i2c-1: unable to read EDID block.
Nov  3 02:49:22 ECO kernel: [59672.002699] i915 0000:00:02.0: LVDS-1: no EDID data
Nov  3 02:49:22 ECO kernel: [59672.073907] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:23 ECO kernel: [59672.565154] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:23 ECO kernel: [59673.016260] i2c-adapter i2c-1: unable to read EDID block.
Nov  3 02:49:23 ECO kernel: [59673.016265] i915 0000:00:02.0: LVDS-1: no EDID data
Nov  3 02:49:26 ECO kernel: [59675.919048] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:27 ECO kernel: [59676.409317] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:27 ECO kernel: [59676.834220] i2c-adapter i2c-1: unable to read EDID block.
Nov  3 02:49:27 ECO kernel: [59676.834226] i915 0000:00:02.0: LVDS-1: no EDID data
Nov  3 02:49:27 ECO kernel: [59676.913321] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:27 ECO kernel: [59677.403661] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:28 ECO kernel: [59677.829195] i2c-adapter i2c-1: unable to read EDID block.
Nov  3 02:49:28 ECO kernel: [59677.829201] i915 0000:00:02.0: LVDS-1: no EDID data
Nov  3 02:49:28 ECO kernel: [59677.941029] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:29 ECO kernel: [59678.432021] [drm] DAC-6: set mode 640x480 0
Nov  3 02:49:29 ECO kernel: [59678.856995] i2c-adapter i2c-1: unable to read EDID block.
Nov  3 02:49:29 ECO kernel: [59678.857000] i915 0000:00:02.0: LVDS-1: no EDID data
Nov  3 02:49:37 ECO pulseaudio[28780]: ratelimit.c: 4 events suppressed
Nov  3 02:49:56 ECO kernel: [59706.456193] [drm] LVDS-8: set mode  13

I never saw anything like this on Jaunty or Intrepid. Why does the System Log get flooded with these *ratelimit.c* warnings, and how is it connected to the freezes? Many thanks to anyone helping me fix this!

---

### Post by phend-one on 2009-11-08
I don't know how to fix it, but I've been getting the same problem as you. Those are the last lines before a kernel panic (Caps lock and Scroll lock blinking).

Fresh install of Karmic. x64. Only started happening today (7th Nov, 2009). 

Very fustrating! Ubuntu was working flawlessly before today! :(

---

### Post by MatchkeY on 2009-11-09
Evening,

  I have the exact same messages in my logs and am also getting the lock-ups. X locks up but the mouse can still be moved.
I can also SSH to the machine from another as well. So it's clearly just X that is locked.

Note; My machine is a laptop and this only happens when I have an external monitor plugged and am running an extended desktop.

at the end of the Xorg log file is the following backtrace;
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0x846400]
3: /usr/lib/xorg/modules/drivers//intel_drv.so [0x3c208a]
4: /usr/bin/X [0x80ced05]
5: /usr/bin/X [0x80cef85]
6: /usr/bin/X(xf86HandleColormaps+0x20d) [0x80cfeed]
7: /usr/lib/xorg/modules/drivers//intel_drv.so [0x3c6b36]
8: /usr/bin/X(AddScreen+0x198) [0x8071c38]
9: /usr/bin/X(InitOutput+0x72e) [0x80b07fe]
10: /usr/bin/X(main+0x1cb) [0x807234b]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1a2b56]
12: /usr/bin/X [0x80719c1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log

other than that nothing else unusual is mentioned in the logs.
It definately feels like a GPU hang.

I'm running Karmic on the following intel graphics card;
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0

Anythoughts would be great.

---

### Post by Johnsie on 2009-11-09
Same problem here. I can move the mouse but nothing is clickable. Happens regularly. Has anyone posted or found a bug report about this? This is my production desktop at work so it needs to be stable.

---

### Post by lelamal on 2009-11-09
> **Johnsie said:**
> Same problem here. I can move the mouse but nothing is clickable. Happens regularly. Has anyone posted or found a bug report about this? This is my production desktop at work so it needs to be stable.

Nope, but I'm doing it now.

Here is [the link to the bug report]("https://bugs.launchpad.net/ubuntu/+bug/479296"). Please, review it and add your contribution there. It would be great if we could provide any information needed to solve this issue as soon as possible.

---

### Post by tomatopa on 2009-12-17
I can reproduce the freezes on either of 2 PCs. I think they're the same as the freezes in this thread .  1. - Same basic setup : Repartition the HD, start with the 9.10 load  line 3 of /var/log/dmesg says this : Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic) -->thats the environment I start with.. 2. - Run the install, then let it do about 159 updates. 3. Get Firefox going, restore my bookmarks. 4. DL thunderbird, get that minimally configured too. 5. Turn on a 'tail -f' of /var/log/syslog. I eventually see the ratelimit messages there, I do not think they're relevant though. 6. Try and listen to an MP3 audio stream, DL 3 packages it wants..  All can go well for hours, maybe a day, maybe 2 hours. Then the GUI just stops responding to clicks.  fyi - (To make a large number of ratelimit messages, pause and unpause the stream) Nothing comes out in syslog as the freeze happens. Reinstalling the fresh has no effect, freezes come back.   When the 'crash' happens : I notice when moving the mouse, mouse still moves but clicks do nothing. After the crash : plugging and unplugging a USB flash drive makes the hard drive rattle, I think the OS is still OK but the GUI is stuck. Also - pushing the numlock key on & off has no effect, I see no light on the kbd.  Hardware #1 (ran ubuntu ver 8 fine) Old Dell, Celeron 2.4G, plenty or ram & hd space, built in NIC and sound and video. I can go get more chipset info if needed. Hardware #3 (ran WinXP fine for years) Old Compaq P4 1.7G, again good specs, built in NIC and sound and video. One last piece of info : I think I tried using the karmic-proposed updates w/ new kernel at least once and still got the freeze.

---

### Post by mric on 2010-06-29
same happened to me with my asus ul30a, crossreferenced to thread [http://ubuntuforums.org/showthread.php?t=1300562&page=18](http://ubuntuforums.org/showthread.php?t=1300562&page=18)

dmesg, messages or syslog doesnt give me much

edit: using Karmic with kernel 2.6.35-020635rc3-generic

---

