---
title: "Sessions closing randomly"
date: 2009-11-08
forum: General Help
---

### Post by steevc on 2009-11-08
My family all have their own accounts on our PC and so we are often all logged in at any time. I upgraded to Karmic yesterday, but since then I have been finding that user sessions are closing for no obvious reason. I've yet to actually see it happen when I've been at the PC, but I found the following in /var/log/syslog

Nov  8 15:03:19 zaphod kdm[1027]: X server for display :1 terminated unexpectedly

Other user sessions will keep going. It may be that only the most recent logged-in session is dying.

Any ideas?

---

### Post by hohensja on 2009-12-23
Hi Steevc

I have the same problem since upgrading to Karmic Koala.
In my case so far only the second session, usaully on VT9, got terminated.

I am trying to reproduce the problem before filing a bug ,but no luck so far.

Did you find a solution yet?

---

### Post by steevc on 2009-12-25
It doesn't seem to be happening in the last week or so. Perhaps an update has fixed it.

It was annoying as it was always my session that crashed. It could have been a certain application I was running, but I don't know which.

I hope your problem clears up too.

---

### Post by steevc on 2010-05-10
This has started happening again. I'm not sure if it happened before I upgraded to 10.04, but getting it regularly now. Happened several times yesterday.

The behaviour is that another user will be using the PC and the screen will go back to the log-in. At that point my session will have closed. It only ever affects my sessions, so there must be something particular about my user settings.

Any suggestions on what to look at?

---

### Post by Zorael on 2010-05-10
**/var/log/Xorg.0.log** (and **Xorg.0.log.old** for the previous session) as well as **/var/log/kdm.log**. It may be that Xorg.0.log only says that the server received a signal to terminate, in which case kdm.log might be of more help.

---

### Post by steevc on 2010-05-13
Seeing the following in kdm.log. Anything useful?

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux zaphod 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: root=UUID=ee66c048-3ab2-425b-a8e2-c609067fc768 ro quiet splash 
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 13 18:31:52 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0252543557/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x7dc410]
3: /usr/lib/libpixman-1.so.0 (0x515000+0x4cf10) [0x561f10]
4: /usr/lib/libpixman-1.so.0 (0x515000+0x147e3) [0x5297e3]
5: /usr/lib/libpixman-1.so.0 (pixman_blt+0x78) [0x54f1e8]
6: /usr/lib/xorg/modules/libfb.so (fbCopyNtoN+0x24d) [0x2ca05d]
7: /usr/bin/X (miCopyRegion+0x21b) [0x819cadb]
8: /usr/bin/X (miDoCopy+0x44d) [0x819cffd]
9: /usr/lib/xorg/modules/libfb.so (fbCopyArea+0x78) [0x2c95c8]
10: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x2bd9000+0x3640b6) [0x2f3d0b6]
Segmentation fault at address 0x5717c

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by Zorael on 2010-05-13
```
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x7dc410]
3: /usr/lib/libpixman-1.so.0 (0x515000+0x4cf10) [0x561f10]
4: /usr/lib/libpixman-1.so.0 (0x515000+0x147e3) [0x5297e3]
5: /usr/lib/libpixman-1.so.0 (pixman_blt+0x78) [0x54f1e8]
6: /usr/lib/xorg/modules/libfb.so (fbCopyNtoN+0x24d) [0x2ca05d]
7: /usr/bin/X (miCopyRegion+0x21b) [0x819cadb]
8: /usr/bin/X (miDoCopy+0x44d) [0x819cffd]
9: /usr/lib/xorg/modules/libfb.so (fbCopyArea+0x78) [0x2c95c8]
10: /usr/lib/xorg/extra-modules/**nvidia_drv.so** (0x2bd9000+0x3640b6) [0x2f3d0b6]
Segmentation fault at address 0x5717c

Caught signal 11 (Segmentation fault). Server aborting
```
Yes, that is the backtrace of a crash. I'm no good at understanding them much myself, but I see **nvidia_drv.so** mentioned there, so this may well be an Nvidia driver issue.

Any driver updates available?


(It could also be a libpixman bug, not sure. You could file a launchpad bug; perhaps then someone with the proper knowhow can interpret your backtrace.)

---

### Post by Bari on 2010-06-06
Hi, I am also getting this problem in Mint9,(I have posted on the mint forum but no answer yet) It is intermittent and seems to happen when I hold down the shift key and then press on the the numeric keys along the top row. Doesn't happen very often (usually towards the end of a long online form) and the numeric key varies. After posting this I have tried holding down shift and pressing the numeric keys in order and on number 2 it closed the session and reverted to the logon screen. Just for your info I have no other users on here. I have not had this happen before when using ubuntu 8 series or mint 7,

---

