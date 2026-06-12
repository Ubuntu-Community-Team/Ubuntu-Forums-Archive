---
title: "RealVNC messed up on Ubuntu 9.04."
date: 2009-09-21
forum: General Help
---

### Post by n0an on 2009-09-21
Hello,

I have been trying to install RealVNC, but the viewer fails to connect to the server. Here's the guide that I used:

```
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
```The host has just given me SSH access, so I am trying to setup VNC. I am done with editing the file for xinetd, but starting xinetd fails. I did a restart instead of stop and start, and it worked.

Anway, here's the problem:

```
root@worldstream-desktop:~# vncviewer localhost:1

VNC viewer for X version 4.0 - built Oct 19 2005 20:19:45
Copyright (C) 2002-2004 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
**vncviewer: unable to open display ""**
```Next, I followed another guide for it, but this time opening the ports gives the same error.

```
[B]Guide
[/B][http://lifehacker.com/317125/set-up-vnc-on-ubuntu-in-four-steps](http://lifehacker.com/317125/set-up-vnc-on-ubuntu-in-four-steps)

**Error**


root@worldstream-desktop:~# x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
22/09/2009 00:50:48 passing arg to libvncserver: -httpport
22/09/2009 00:50:48 passing arg to libvncserver: 5800
22/09/2009 00:50:48 -usepw: found /root/.vnc/passwd
22/09/2009 00:50:48 x11vnc version: 0.9.3 lastmod: 2007-09-30
22/09/2009 00:50:48
22/09/2009 00:50:48 *** XOpenDisplay failed. No -display or DISPLAY.
22/09/2009 00:50:48 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
22/09/2009 00:50:48 *** 1 2 3 4
No protocol specified
22/09/2009 00:50:52

22/09/2009 00:50:52 ***************************************
22/09/2009 00:50:52 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

```Now what to do?

Also, while trying to run VNCViewer for Port 5090, I get an error "read: Connection reset by peer (10054)".

Thanks!

---

### Post by Iowan on 2009-09-21
[Another]("http://www.linuxquestions.org/questions/ubuntu-63/how-to-install-realvnc-on-jaunty-741268/?") How-To that might be helpful.

---

### Post by n0an on 2009-09-21
I used that thread to configure the initial steps correctly, but it gives dependency errors while installing libstdc++6-pic, libstdc++6-dev, and gcc-3.4 and g++-3.4.

g++-3.4 installation gives an error prompting to install libstdc++6-dev, but on doing so it asks for g++ :confused:.
It's like a maze in here now.

On doing ./vncviewer ./usr/.. it gives this error:

> Can't install manual pages to /usr/local/man/man1
Xvnc hasn't changed
vncviewer hasn't changed
vncpasswd hasn't changed
vncconfig hasn't changed
vncserver hasn't changed
x0vncserver hasn't changed

---

