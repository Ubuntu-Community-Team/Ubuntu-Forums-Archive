---
title: "System Crash"
date: 2009-08-25
forum: General Help
---

### Post by p110011 on 2009-08-25
I just installed Jaunty on an older pc, which I recently used with Hardy Heron for over a year.
I have it set up pretty much how it was, but now every time the screen saver starts, it crashes, (completely freezes) or sometimes if I watch a streamed video from the net, it logs me out.

This is my system log:
```
Aug 25 07:30:01 mustang /USR/SBIN/CRON[9292]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Aug 25 07:30:01 mustang /USR/SBIN/CRON[9307]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 25 07:30:02 mustang anacron[9343]: Anacron 2.3 started on 2009-08-25
Aug 25 07:30:02 mustang anacron[9343]: Normal exit (0 jobs run)
Aug 25 07:30:07 mustang kernel: [ 3531.528158] #
Aug 25 07:30:13 mustang x-session-manager[3129]: WARNING: Detected that screensaver has left the bus 
Aug 25 07:30:14 mustang gdm[2805]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Aug 25 07:30:14 mustang console-kit-daemon[2563]: WARNING: Unable to activate console: No such device or address 
Aug 25 07:30:15 mustang acpid: client 2809[0:0] has disconnected 
Aug 25 07:30:15 mustang acpid: client connected from 9605[0:0] 
Aug 25 07:30:15 mustang kernel: [ 3539.508755] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
Aug 25 07:30:15 mustang kernel: [ 3539.508784] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Aug 25 07:30:15 mustang kernel: [ 3539.508835] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Aug 25 07:30:15 mustang kernel: [ 3539.722155] [drm] Setting GART location based on new memory map
Aug 25 07:30:15 mustang kernel: [ 3539.722168] [drm] Loading R200 Microcode
Aug 25 07:30:15 mustang kernel: [ 3539.722219] [drm] writeback test succeeded in 1 usecs
Aug 25 07:30:17 mustang kernel: [ 3541.620148] #
Aug 25 07:30:29 mustang kernel: [ 3553.204157] #
Aug 25 07:30:36 mustang pulseaudio[9734]: pid.c: Stale PID file, overwriting.
Aug 25 07:30:36 mustang kernel: [ 3560.768156] #
Aug 25 07:30:37 mustang pulseaudio[9734]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 25 07:30:37 mustang pulseaudio[9734]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Aug 25 07:30:37 mustang pulseaudio[9734]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 25 07:30:37 mustang pulseaudio[9734]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 25 07:30:37 mustang pulseaudio[9734]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 22050 Hz.
Aug 25 07:30:37 mustang pulseaudio[9734]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Aug 25 07:30:39 mustang kernel: [ 3562.816782] #
Aug 25 07:30:40 mustang kernel: [ 3563.852154] #
Aug 25 07:30:40 mustang x-session-manager[9672]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
```Not sure if that is the problem, but I could use some help if something is not configured proper.

TIA,

Gill

---

### Post by P4man on 2009-08-25
You got an ATI R200 videocard. That one is no longer supported by ATI, and as a result, the binary drivers dont work with it (did you try nonetheless?). You can only use the opensource "ati" driver, which is .. not quite stellar yet when you need 3D acceleration or video acceleration.

If you are using binary ATI drivers, you'll need to revert to the opensource one's. If those aren't good enough for you, you can only revert back to ubuntu 8.10 and use the older binary ATI drivers which do support that version of XORG, or replace the videocard...

---

### Post by p110011 on 2009-08-25
OK, thanks for the quick reply, I'll look for a replacement. Not ATI as it seems that it causes too much conflict.

Oh, if I pop a different card in will it just work? I mean, if I can find one that is supported. Or do I need to uninstall and reconfigure anything?

Thanks again,

Gill

---

### Post by P4man on 2009-08-25
Depends. If you installed the binary drivers, then  you'll have to remove those if you install an nVidia card, or X won't boot. 

If you are using the default drivers, then I think it will just work if you plug in any other videocard. At worst, you'll have to drop to a TTY and edit xorg.conf.

---

### Post by p110011 on 2009-08-25
I did not install any drivers.
I found some 6200 AGP GeForce 256MB Graphics Cards on craigslist (on the cheep) so it looks like I'll give that a go. Thanks!

---

### Post by P4man on 2009-08-25
well, if you didnt install any drivers, then even with an ATI R200 it shouldn't be crashing... opensource ati drivers may not be very fast, but I havent found them particularly buggy. So pls dont blame me if you buy a new card and it doesnt help :s

---

### Post by p110011 on 2009-08-25
No problem, I just misunderstood what you where saying about the drivers.

I guess I'll have to figure out what the problem is then.

---

### Post by p110011 on 2009-08-27
Hey P4man, I found a GeForce 6200 256MB DDR2 AGP on craigslist for $25.00 (I normally steer clear of used pc stuff) and this thing is SMOKING FAST! Ha ha 

I have all kinds of eye candy running, and my screen saver is not crashing, thanks.

---

### Post by P4man on 2009-08-28
"smoking fast" is a bit of an overstatement :)
Have a look at this chart:

[http://www.tomshardware.com/charts/gaming-graphics-charts-q3-2008/Sum-of-FPS-Benchmarks-Totals,795.html](http://www.tomshardware.com/charts/gaming-graphics-charts-q3-2008/Sum-of-FPS-Benchmarks-Totals,795.html)

A 6200 would probably be around half the speed of 7300.
But indeed any discrete card will be insanely fast compared to non accelerated onboard video :)

---

