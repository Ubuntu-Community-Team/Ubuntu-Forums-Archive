---
title: "upgrade of X to 6.8.2-77 breaks working system"
date: 2006-05-08
forum: General Help
---

### Post by martyFouts on 2006-05-08
Last week I upgraded a 5.10 x86 system to dual monitor status and installed the Nvidia proprietary driver. This worked fine until Friday, when I used apt-get to update X to 6.8.2-77.  Now X refuses to start. The X.org.log file looks fine, but if you start X using startx, the output is:

root@sponge:/etc# init.d/gdm stop
 * Stopping GNOME Display Manager...                                                                                             [ ok ]
root@sponge:/etc# startx
xauth:  creating new authority file /root/.serverauth.10900

X Window System Version 6.8.2 (Ubuntu 6.8.2-77.1 20060503192905 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.12 i686 [ELF]
Current Operating System: Linux sponge.danger.com 2.6.12-10-386 #1 Fri Apr 28 13:13:44 UTC 2006 i686
Build Date: 03 May 2006
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Fri Apr 28 13:13:44 UTC 2006 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May  8 19:07:14 2006
(==) Using config file: "/etc/X11/xorg.conf"

Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.


Any explanation of why I'm getting connection reset by peer and what I should do about it would be greatly appreciated.

---

