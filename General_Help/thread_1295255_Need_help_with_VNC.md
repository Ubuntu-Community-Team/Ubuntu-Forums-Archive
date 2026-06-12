---
title: "Need help with VNC"
date: 2009-10-19
forum: General Help
---

### Post by Markstar on 2009-10-19
Hi,
I finished installing my Ubuntu home server (9.04 + IceWM) and I would like to be able to control it via VNC. I installed the tightvncserver and ran it. It asked me for a password and that was it. However, I still can't connect to it (neither from the server nor another computer). 

This is *~/.vnc/xstartup*:
```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
/etc/X11/Xsession
```

And this is *~/.vnc/e6700:1.log* (e6700 being the name of my machine):
```
19/10/09 15:29:23 Xvnc version TightVNC-1.3.9
19/10/09 15:29:23 Copyright (C) 2000-2007 TightVNC Group
19/10/09 15:29:23 Copyright (C) 1999 AT&T Laboratories Cambridge
19/10/09 15:29:23 All Rights Reserved.
19/10/09 15:29:23 See http://www.tightvnc.com/ for information on TightVNC
19/10/09 15:29:23 Desktop name 'X' (e6700:1)
19/10/09 15:29:23 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
19/10/09 15:29:23 Listening for VNC connections on TCP port 5901
xrdb: No such file or directory
xrdb: can't open file '/home/markstar/.Xresources'
```

So xrdb is the X resource database manager, but I don't really know what I am supposed to do here. The only thing I noticed was that the last line says /etc/X11/Xsession, which does not exist here (only /etc/X11/Xsession.d exists). :(

Can anybody tell me what I'm doing wrong?

Thank you in advance!

**Edit:** I have also tried this with my normal Ubuntu Desktop. I get the xrdb error on both computers.

---

