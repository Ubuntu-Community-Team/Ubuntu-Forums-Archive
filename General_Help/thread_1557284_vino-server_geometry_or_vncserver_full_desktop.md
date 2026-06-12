---
title: "vino-server geometry or vncserver full desktop"
date: 2010-08-20
forum: General Help
---

### Post by ZequeZ on 2010-08-20
Hi ^^, I have activated the option to share my desktop so I can connect from another computer..

The default ubuntu VNC server is vino-server, the problem is that I think it doesn't support geometry/resolution changes. Can anyone confirm this?

The other option I have is the vncserver (or vnc4server? I don't know), the problem is that when I connect to it, it only show a grey screen with a console window in the center... So, how can I share the whole desktop?

---

The client I'm using is the xvnc4client.

Hope someone can help me =/
Thanks ^^

---

### Post by ZequeZ on 2010-08-20
Ok I solved it, partially:

I'm using vncserver.

I read somewhere I had to edit the ~/.vnc/xstartup file, at the top of the file there is this:

```

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

```Great! So I uncommented that and I tought it would work. But no, the same that before

When I checked the log files ~/.vnc/my-computer:1.log and I found this line:
```

exec: 5: /etc/X11/xinit/xinitrc: Permission denied
```So I tried to start vncserver as root, bad idea, didn't work.

Then I checked the content of xinitrc:

```
#!/bin/bash

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
```So I copy the route ./etc/X11/Xsession to the xstartup file, and I make this modifications:
```

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
exec /etc/X11/Xsession
```Then I started the vncserver and then I connected to it and I had a gnome session ^^

Hope this little "guide" help someone ^^

--------------------

The only problem is that the session created is a new gnome session... There is a way to use the actual gnome session?

Thanks ^^

EDIT: x11vnc do the work ^^. And I guess all VNC servers use the same configuration files? Am I right?

EDIT2: If you have slow problems with x11vnc use -noxdamage ;) and use -geometry WxH to change resolution ):P

---

### Post by krunge on 2010-08-22
> **ZequeZ said:**
> 
EDIT: x11vnc do the work ^^. And I guess all VNC servers use the same configuration files? Am I right?

x11vnc certainly does not use any of the other vnc servers' config files.
> 
EDIT2: If you have slow problems with x11vnc use -noxdamage ;) and use -geometry WxH to change resolution ):P
Yes, it is sad this bug in Xorg and/or video drivers has been around for so long.  XDAMAGE is a good idea, but the implementation is buggy and no one seems to want to fix it.

---

