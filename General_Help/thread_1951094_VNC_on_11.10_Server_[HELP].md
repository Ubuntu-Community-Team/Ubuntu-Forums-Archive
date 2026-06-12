---
title: "VNC on 11.10 Server [HELP]"
date: 2012-04-01
forum: General Help
---

### Post by denzelchurchill on 2012-04-01
I just can't seem to get VNC to work on 11.10 server. All I get is the grey/black screen with an X for a pointer. Am I missing some config? I've tried dozens of ~/.vnc/xstartup variations from some Googling. No luck yet. Would be grateful for any help.

"First try" - I get black/grey screen with X for a pointer.
"Second try" - I get beige screen with X for a pointer and a "Failed to load 'ubuntu'" error.

Thanks,
Bill


OS: Ubuntu 11.10 Server (fresh install)
Packages installed since: tightvncserver, gnome-core (and openssh and samba)
Config / debug info below



~/.vnc/xstartup (first try)

    #!/bin/sh
    
    xrdb $HOME/.Xresources
    xsetroot -solid grey
    #x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
    #x-window-manager &
    # Fix to make GNOME work
    export XKL_XMODMAP_DISABLE=1
    /etc/X11/Xsession

tightvncserver log (first try)

    01/04/12 20:09:25 Xvnc version TightVNC-1.3.9
    01/04/12 20:09:25 Copyright (C) 2000-2007 TightVNC Group
    01/04/12 20:09:25 Copyright (C) 1999 AT&T Laboratories Cambridge
    01/04/12 20:09:25 All Rights Reserved.
    01/04/12 20:09:25 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
    01/04/12 20:09:25 Desktop name 'X' (myservername:1)
    01/04/12 20:09:25 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
    01/04/12 20:09:25 Listening for VNC connections on TCP port 5901
    Font directory '/usr/share/fonts/X11/Type1/' not found - ignoring
    Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
    Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
    xrdb: No such file or directory
    xrdb: can't open file '/home/username/.Xresources'

    01/04/12 20:09:33 Got connection from client 192.168.1.127
    01/04/12 20:09:33 Using protocol version 3.8
    01/04/12 20:09:33 Full-control authentication passed by 192.168.1.127
    01/04/12 20:09:33 Pixel format for client 192.168.1.127:
    01/04/12 20:09:33   32 bpp, depth 24, little endian
    01/04/12 20:09:33   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
    01/04/12 20:09:33   no translation needed
    01/04/12 20:09:33 rfbProcessClientNormalMessage: ignoring unknown encoding 16
    01/04/12 20:09:33 Using tight encoding for client 192.168.1.127
    01/04/12 20:09:33 rfbProcessClientNormalMessage: ignoring unknown encoding 8

~/.vnc/xstartup (second try)

    #!/bin/sh

    # Uncomment the following two lines for normal desktop:
    unset SESSION_MANAGER
    exec sh /etc/X11/xinit/xinitrc
    
    [ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
    [ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
    xsetroot -solid grey
    vncconfig -iconic &
    x-terminal-emulator -geometry 1280x720+10+10 -ls -title "$VNCDESKTOP Desktop" & gnome-session &


tightvncserver log (second try)

    01/04/12 19:58:02 Xvnc version TightVNC-1.3.9
    01/04/12 19:58:02 Copyright (C) 2000-2007 TightVNC Group
    01/04/12 19:58:02 Copyright (C) 1999 AT&T Laboratories Cambridge
    01/04/12 19:58:02 All Rights Reserved.
    01/04/12 19:58:02 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
    01/04/12 19:58:02 Desktop name 'X' (myservername:1)
    01/04/12 19:58:02 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
    01/04/12 19:58:02 Listening for VNC connections on TCP port 5901
    Font directory '/usr/share/fonts/X11/Type1/' not found - ignoring
    Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
    Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
    sh: Can't open /etc/X11/xinit/xinitrc
    
    01/04/12 19:59:20 Got connection from client 192.168.1.127
    01/04/12 19:59:20 Using protocol version 3.8
    01/04/12 19:59:20 Full-control authentication passed by 192.168.1.127
    01/04/12 19:59:20 Pixel format for client 192.168.1.127:
    01/04/12 19:59:20   32 bpp, depth 24, little endian
    01/04/12 19:59:20   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
    01/04/12 19:59:20   no translation needed
    01/04/12 19:59:20 rfbProcessClientNormalMessage: ignoring unknown encoding 16
    01/04/12 19:59:20 Using tight encoding for client 192.168.1.127
    01/04/12 19:59:20 rfbProcessClientNormalMessage: ignoring unknown encoding 8


EDIT: X for a pointer on both attempts.

---

### Post by Azdour on 2012-04-02
Hi,

I use vnc4server and I had to alter the xstartup to:

```
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &

```

vnc4server does not add the gnome-session and that results in a grey screen and no desktop. Hope this helps.

---

### Post by denzelchurchill on 2012-04-02
Thanks Adzour! I'll try this tonight.

Have you given NX a try? Considering going down that route at this point...

---

### Post by Azdour on 2012-04-03
Hi,

I have used the FreeNX and I it performs better then VNC. If I ever had to just use something for remote admin I would probably us it.
The reason we stick to VNC at the moment is that we need to remote into a users desktop to give them support.

---

### Post by denzelchurchill on 2012-04-03
So... I gave your xstartup a try...no dice. It was the same as I had, without the first two lines. Gave me a terminal window, but got the same error message on top of it.

What's peculiar is that I gave FreeNX a try and got the same exact error as with VNC... "failed to load session "ubuntu""

What on earth is going on here? The GUI loads fine on display 0 (my desktop monitor that I have set up until I can get this working entirely via remote). Graphics driver issues? I'm really lost at this point...

---

### Post by Azdour on 2012-04-03
Hi,

Ubuntu 11.10 comes with the lightdm display manager. I've tried to get vnc4server to work on a virtualbox install of 11.10. and I'm also getting just a grey window with an 'X' when I call lightdm in my xstartup. When I use gnome-session I get a desktop but no menus. I'm not getting the the 'failed to load session'. I'm not sure what to suggest but I can see that VNC does not seem to work well on Ubuntu 11.10

I wonder if the following thread offers any light for you:

[http://ubuntuforums.org/showthread.php?p=11370136](http://ubuntuforums.org/showthread.php?p=11370136)

---

### Post by drinxtir on 2012-04-06
I had to use  'vncserver -x RandR' and call gnome-panel to get a decent desktop. Just started playig with vnc today..

---

