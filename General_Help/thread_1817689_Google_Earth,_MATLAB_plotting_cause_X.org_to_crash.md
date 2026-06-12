---
title: "Google Earth, MATLAB plotting cause X.org to crash and return to login; best fix?"
date: 2011-08-03
forum: General Help
---

### Post by jpardey on 2011-08-03
Hello,

As mentioned in the subject, whenever I start google earth, or try to plot something in MATLAB, I find myself returned to the login screen. There's nothing usable in any log file, nor does any program give an error message. I've been running 64 bit Ubuntu since 8 or 9, and I'm on 11.04 currently. I had some similar errors previous to 10.10 or so, and it seems to have only recently come back. I have an Nvidia 8600GT, and nvidia driver 270.41.06.

I know this is a fairly common problem (even across graphics cards, kernels, 64/32, distros, etc), but all the fixes around seem to involve various ppa's that don't exist any more, or forcing x server downgrades. Is there any way to diagnose what is happening within X, to simplify fixing this kind of thing, or does anyone have a fairly clean and ubuntu-upgrade resilient way of fixing this? Not being able to use MATLAB is a bit of a showstopper for me here.

Thanks!

---

### Post by Gyokuro on 2011-08-03
Hi,

I can only speak for MATLAB but in my experience it's very resource hungry and afaik you need at least 3GB RAM only for MATLAB and all machines where MATLAB got used had at least 8GB of RAM on RHEL 5.x or Debian 5/Ubuntu LTS systems and the same goes for the NVidia cards: some kind of NVidia Quadro were used. Therefore I suggest to use an Ubuntu LTS release. Are there no errors logged in /var/log/syslog??

---

### Post by jpardey on 2011-08-03
For anyone with the same problems, I just found [https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing) which I wish I'd seen before... Going to try running without the nvidia drivers at some point.

---

### Post by jpardey on 2011-08-03
Oh hey Gyokuro, didn't see your reply... if matlab can't handle plotting 2 1d vectors, each 200 elements long, with 2g ram, I'd be very surprised. Running the same commands from console showed an exception, but only because there was no longer an X server running. google earth used to run just fine, so it's a recent update to x.org, I'd think. Thanks though! LTS does sound smart... No great fan of unity and all that.

---

### Post by jpardey on 2011-08-08
Found this in /var/log/gdm/:0.log-1 or whatever it is...

```
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x26) [0x4a2656]
1: /usr/bin/X (0x400000+0x621ca) [0x4621ca]
2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f0921b4a000+0xfc60) [0x7f0921b59c60]
3: /usr/bin/X (0x400000+0x2f4be) [0x42f4be]
4: /usr/bin/X (ProcessWorkQueue+0x21) [0x4325d1]
5: /usr/bin/X (WaitForSomething+0x68) [0x45c668]
6: /usr/bin/X (0x400000+0x2e032) [0x42e032]
7: /usr/bin/X (0x400000+0x21a7e) [0x421a7e]
8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xff) [0x7f0920a93eff]
9: /usr/bin/X (0x400000+0x21629) [0x421629]
Segmentation fault at address 0x13c2898a8

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) Power Button: Close
(II) Unloading evdev
(II) Power Button: Close
(II) Unloading evdev
(II) Logitech USB Optical Mouse: Close
(II) Unloading evdev
(II) AT Translated Set 2 keyboard: Close
(II) Unloading evdev
 ddxSigGiveUp: Closing log
```

Also found something in the X log about not being able to load the nvidia module. It suggested the kernel logs, where I couldn't find anything. I very clearly have hardware acceleration working with SDL at least, and Unity was working (using GNOME 2 now), so I don't know if that has anything to do with anything.

---

### Post by jpardey on 2011-08-21
[https://bugs.launchpad.net/xorg-server/+bug/794895](https://bugs.launchpad.net/xorg-server/+bug/794895) seems to have been the culprit, for anyone who sees this. I just commented out 'FontPath "unix/:7100"' and restarted X. Works fine! Still would be nice to find out what's going on.

---

