---
title: "X server not starting on linux shrike 9.0"
date: 2005-03-15
forum: General Help
---

### Post by wambuzz on 2005-03-15
Hi,
  Ive installed Linux shrike 9.0 and I having problems starting x server.This is the error I get when I type in # startx......


[root@apps11isrv X11]# redhat-config-xfree86
Couldn't start X server, trying with a fresh configuration
Trying with card: S3 Savage4
Error, cannot start X server.
[root@apps11isrv X11]# startx
Using authority file /root/.Xauthority
Writing authority file /root/.Xauthority
Using authority file /root/.Xauthority
Writing authority file /root/.Xauthority

XFree86 Version 4.3.0 (Red Hat Linux release: 4.3.0-2)
Release Date: 27 February 2003
X Protocol Version 11, Revision 0, Release 6.6
Build Operating System: Linux 2.4.20-3bigmem i686 [ELF]
Build Date: 27 February 2003
Build Host: porky.devel.redhat.com

        Before reporting problems, check [http://www.XFree86.Org/](http://www.XFree86.Org/)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.4.20-8 (bhcompile@porky.devel.redhat.com) (gcc version 3.2.2 20030222 (Red Hat Linux 3.2.2-5)) #1 Thu Mar 13 17:54:28 EST 2003
Markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/XFree86.0.log", Time: Tue Mar 15 11:28:25 2005
(==) Using config file: "/etc/X11/XF86Config"

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.


Please help!!!!!!!!! :(

---

