---
title: "Other Display Managers don't work"
date: 2010-08-20
forum: General Help
---

### Post by ScarletWyvern on 2010-08-20
So, I decided to replace GDM with another display manager because I honestly don't really like GDM at all.

I tried to install SLiM first, since I thought it looked nice. On boot, start up will get to "Starting X display manager (slim)" and it will stop there. SLiM never loads. slim.log reads:

```
/usr/bin/X11/xauth:  creating new authority file /var/run/slim.auth


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux Alouette 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=dc0b55d3-c896-49e3-bc86-2dc37dcc5ad9 ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 20 14:06:53 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) intel(0): [drm] failed to set drm interface version.
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): failed to get resources: Bad file descriptor
(EE) intel(0): Kernel modesetting setup failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```Then, I decided to try LXDM. Upon installing and configuring LXDM, start up still reads "Starting X display manager (slim)" but GDM loads, albeit extremely buggy with screen flickering and all kinds of nasty things. lxdm.log reads:

```
start X

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
catch signal 15
```So far, GDM has been the only DM that runs properly. I can't figure out why.

---

### Post by ScarletWyvern on 2010-08-20
Bump?

---

### Post by ScarletWyvern on 2010-08-20
: (

---

### Post by ScarletWyvern on 2010-08-20
No one can help me?

---

### Post by ScarletWyvern on 2010-08-20
I've been searching all day. Someone's got to have an answer.

---

### Post by ScarletWyvern on 2010-08-21
I did the work around I found here: [http://web.archiveorange.com/archive/v/LLXmLyd1jDtopQV8eYti](http://web.archiveorange.com/archive/v/LLXmLyd1jDtopQV8eYti)

Now, SLiM loads, but when I try to log in, X segfaults with the following message in slim.log:

```
/usr/bin/X11/xauth:  creating new authority file /var/run/slim.auth


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux Alouette 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=dc0b55d3-c896-49e3-bc86-2dc37dcc5ad9 ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 21 04:22:32 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
/usr/bin/X11/xauth:  creating new authority file /home/wyvern/.Xauthority
(EE) intel(0): Couldn't create pixmap for fbcon
(EE) intel(0): failed to set mode: Operation not permitted
Backtrace:
0: /usr/bin/X11/X (xorg_backtrace+0x3b) [0x80e938b]
1: /usr/bin/X11/X (0x8048000+0x61c8d) [0x80a9c8d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xcbc410]
3: /usr/bin/X11/X (xf86ProbeOutputModes+0xfa) [0x80cef2a]
4: /usr/bin/X11/X (0x8048000+0x8e0f0) [0x80d60f0]
5: /usr/bin/X11/X (RRGetInfo+0xa1) [0x810a7a1]
6: /usr/bin/X11/X (0x8048000+0x8ca2a) [0x80d4a2a]
7: /usr/bin/X11/X (0x8048000+0x138801) [0x8180801]
8: /usr/lib/xorg/modules/extensions/libglx.so (0x2d1000+0x427b4) [0x3137b4]
9: /usr/bin/X11/X (xf86Wakeup+0x513) [0x80b5d53]
10: /usr/bin/X11/X (WakeupHandler+0x52) [0x80779f2]
11: /usr/bin/X11/X (WaitForSomething+0x1a2) [0x80a3fa2]
12: /usr/bin/X11/X (0x8048000+0x2a1b0) [0x80721b0]
13: /usr/bin/X11/X (0x8048000+0x1ed7a) [0x8066d7a]
14: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0xaf3bd6]
15: /usr/bin/X11/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address 0x10

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by izod1991 on 2010-12-22
I'm having the same problem. I installed Ubuntu 10.10 (Netbook Remix), and decided I'd rather have fluxbox running on it than Gnome or KDE. After I got fluxbox running, I tried getting a different window manager (LXDM or SLiM), but neither works - it's the same symptoms & error messages that you have.

Anyone have a clue what's up with this? Surely there's a way to use an alternative window manager - are we all stuck with GDM forever? #-o

---

### Post by nikhil760 on 2010-12-25
I have the same problem and now I don't know how to revert back to gdm. Even removing slim and reinstalling gdm from terminal could not fix the issue.

For now, I switch to console using Alt+Ctrl+F1, login and run 'sudo gdm start'

I was spoilt for choice in Arch linux, but this is no fun in Ubuntu. :mad:

Resolved
sudo dpkg-reconfigure gdm

---

