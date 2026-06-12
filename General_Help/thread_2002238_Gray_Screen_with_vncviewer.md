---
title: "Gray Screen with vncviewer"
date: 2012-06-12
forum: General Help
---

### Post by aLearner on 2012-06-12
First, I realize that this question has been asked many times and I've spent time looking for answers in threads like this one

[http://ubuntuforums.org/showthread.php?t=1788419]("http://ubuntuforums.org/showthread.php?t=1788419")

and this one

[http://ubuntuforums.org/showthread.php?t=1236957]("http://ubuntuforums.org/showthread.php?t=1236957")

and countless others on the net but with no luck.

So, here's what I've been trying to do. I have two machines running Ubuntu. Machine # 1 has Ubuntu 11.10 and Machine # 2 has Ubuntu 12.04. Both machines are NOT on the same LAN. I'm trying to run vncserver on Machine # 2 and connect to it using vncviewer on Machine # 1 (over the internet). I configured Machine # 2 after reading the following webpage

[http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html]("http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html")

Then, on Machine # 2, I type

```
vncserver -geometry 800x600
```

and then one Machine # 1, I type

```
vncviewer XXX.XXX.XXX.XXX:2
``` 

(where XXX.XXX.XXX.XXX is the IP address Machine # 2). But all I see is a grayish-black screen on Machine # 1. Please see the enclosed picture for an idea of how the grayish-black screen looks. From peering at the other threads on the net, it appears that the file

```
~/.vnc/xstartup
``` 

is important. I'm enclosing the version I currently have (after trying many configurations) below this message. I'm also enclosing the log file that's generated.

Any help in getting things to work would be greatly appreciated.

Thank you.

---- BEGIN LOG FILE OUTPUT -----
```

Xvnc Free Edition 4.1.1 - built Feb  5 2012 20:04:02
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Tue Jun 12 07:15:07 2012
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!

Tue Jun 12 07:15:19 2012
 Connections: accepted: 0.0.0.0::54440
 SConnection: Client needs protocol version 3.8

Tue Jun 12 07:15:20 2012
 SConnection: Client requests security type VncAuth(2)

Tue Jun 12 07:15:25 2012
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565

Tue Jun 12 07:15:26 2012
 VNCSConnST:  Client pixel format depth 24 (32bpp) little-endian rgb888

```
---- END LOG FILE OUTPUT -----

---- BEGIN ~/.vnc/xstartup FILE -----
```

#!/bin/sh

#Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
. /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager

```
---- END ~/.vnc/xstartup FILE -----

---

### Post by aLearner on 2012-06-13
Just in case anyone is following this thread. I tried running vncserver again with the following command

```
vncserver :3 -geometry 800x600
```

and this time when I fired up vncviewer like this

```
vncviewer XXX.XXX.XXX.XXX:3
```

I could see things just fine (I get a KDE desktop)! Great! I didn't change anything at my end so I have no idea why it's working now. However, when I fire up vncserver with the following command

```
vncserver :2 -geometry 800x600
```

and then use vncviewer, things don't work. 

So, I'm wondering why things work with :3 and not with :2.

---

### Post by HermanAB on 2012-06-13
OK, so has your system been hacked yet?

VNC should not be lightly discarded, it should be thrown, with great force.  Rather kill VNC while your machine is still unbreached and use SSH - it can do everything VNC does and much more, securely.

---

### Post by vv1984 on 2012-12-26
> **HermanAB said:**
> OK, so has your system been hacked yet?

VNC should not be lightly discarded, it should be thrown, with great force.  Rather kill VNC while your machine is still unbreached and use SSH - it can do everything VNC does and much more, securely.

How do i get a GUI with ssh stand alone?
I understand your point, but VNC is the only way i can get a graphical remote connection to my ubuntu server so far.

Thank you

---

### Post by CeltaWeb on 2012-12-26
> **vv1984 said:**
> How do i get a GUI with ssh stand alone?

You might want to have a look at this post.

[http://ubuntuforums.org/showthread.php?t=2053541](http://ubuntuforums.org/showthread.php?t=2053541)

> On 12.04 here Nautilus (the default file explorer) has a "Connect to  Server..." entry in its File menu that gives the option to use SSH to  connect to a remote server.

---

