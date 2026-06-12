---
title: "karmic 9.1 never completes boot"
date: 2010-03-16
forum: General Help
---

### Post by kjtruitt on 2010-03-16
System has been working fine until recently bootups started taking longer and longer. Finally the other day after waiting 15 minutes or so I gave up.

I was able to log in with the xfce option (small command line with no
windowing support).  From this I observed that I could run all my programs (but without windowing support) and that the system seemed generally healthy (as did the hard drive).

I found /etc/Xsession and ran 
```
sudo ./Xsession
```

This successfully loaded X (is that it?) rather quickly, but everything was
running as root.  That's what I'm in on now.  

So it seems that there's some kind of problem with an init script failing to load X at some point.  Or it could be more complex.  Any ideas?

Specifically, the computer presented the login option for the gui and I logged in as my non-root user.  Then I got the swirling lights with the
bird in flight background (dark blue).  It never progresses beyond this,
and the hard drive is whirring consistently until I shut the computer off.

Thanks

---

### Post by prodigy_ on 2010-03-16
Check your Xorg logs in /var/log.

---

### Post by kjtruitt on 2010-03-18
Here's the tail of an Xorg log.  I should mention that the xfce boot symptoms have changed slightly since I've been logging in with xterm sessions--now if I attempt an xfce session, there is a slight pause after entering my password, then the user dialog opens again.

------------------------
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0x4f8400]
3: /usr/bin/X(FreeClientResources+0xdf) [0x8074a1f]
4: /usr/bin/X(FreeAllResources+0x60) [0x8074af0]
5: /usr/bin/X(main+0x3c5) [0x8072545]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x646b56]
7: /usr/bin/X [0x80719c1]
Saw signal 11.  Server aborting.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) TPPS/2 IBM TrackPoint: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

---

### Post by kjtruitt on 2010-03-23
I was hoping to avoid having to reinstall the system, but clearly that's what I'm going to have to do.

In fact I was hoping there might be a way to use my install cd to reload the parts of the system that were broken and save me the trouble of backing up my files and re-downloading the myriad software files I've installed.  That *should* be how it works.  But now I'll resort to the cave man option.

---

