---
title: "Can't login! Help!"
date: 2011-05-31
forum: General Help
---

### Post by arsci on 2011-05-31
Hey everyone, I'm having a bit of an issue. I was transferring some files from an external hard drive onto my desktop computer running ubuntu 10.04...It filled up the hard drive to the max, rebooted and I couldn't login. Did some googling and thought it might be because it was too full so I plugged the ubuntu HDD into my laptop, removed some files and tried again. Still no luck.

What it does is tries to automatically login (that's how I have it set) at the main login prompt, it for some reason is not able to and the screen flickers a bit and shows the login screen. I enter my username and password and it flickers really quick and goes back to the login screen. Does this for my other user account as well. I can login via the command prompt (ctl-alt-f7) and do stuff there, but I cannot login to the GUI. 

Can anyone help me out?

Thanks in advance,

Ryan

---

### Post by Zorael on 2011-05-31
Hm, that still sounds like a space issue to me. Try booting into recovery mode and picking **clean packages**, or something along those lines. You can do the same from a console with '**sudo apt-get clean**'.

---

### Post by arsci on 2011-05-31
I tried sudo apt-get clean and it didn't change anything.

---

### Post by Zorael on 2011-05-31
All right.

If you run '**df -h**', does it say you have space left on your root and home partitions (if separate)?

Is there any interesting output at the end of Xorg's log; **/var/log/Xorg.0.log**?
'**tail -20 /var/log/Xorg.0.log**' should list the last 20 lines.

Likewise, anything of interest in kdm's log; **/var/log/kdm.log**?
'**tail -20 /var/log/kdm.log**'.

---

### Post by arsci on 2011-05-31
okay, df -h says each filesystem is 0% or 1% except for /dev/sbd1 which is at 57%

Here is 'tail -20 /var/log/Xorg.0.log'

```

(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

Here is 'tail -20 /var/log/kdm.log'

```

Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=bed6242c-ab56-4f13-bd64-a4010540682c ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 31 11:37:03 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(II) [KMS] Kernel modesetting enabled.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0660223356/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QThread::wait: Thread tried to wait on itself
QThread: Destroyed while thread is still running
KCrash: Application 'kdmgreet' crashing...
Fatal Error: Accessed global static 'KGlobalPrivate *globalData()' after destruction. Defined at ../../kdecore/kernel/kglobal.cpp:116
Unable to start Dr. Konqi
 ddxSigGiveUp: Closing log

```

---

### Post by Zorael on 2011-05-31
```
QThread::wait: Thread tried to wait on itself
QThread: Destroyed while thread is still running
KCrash: Application 'kdmgreet' crashing...
[COLOR="Red"]**Fatal Error: Accessed global static 'KGlobalPrivate *globalData()' after destruction. Defined at ../../kdecore/kernel/kglobal.cpp:116**[/COLOR]
Unable to start Dr. Konqi
 ddxSigGiveUp: Closing log
```
Interesting. Googling that line turns up with a bunch of stuff.

Could you take a look at your **~/.xsession-errors** too? Anything interesting there? A tail -20 might be too small an interval (20 lines) to catch everything.

Is dbus running, and hal and/or udev?
```
$ ps axo pid,user,comm | egrep "dbus|hal|udev"
```

---

