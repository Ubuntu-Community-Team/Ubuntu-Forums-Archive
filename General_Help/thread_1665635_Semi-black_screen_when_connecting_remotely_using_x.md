---
title: "Semi-black screen when connecting remotely using xtightvncviewer"
date: 2011-01-12
forum: General Help
---

### Post by sleepee on 2011-01-12
I have a weird problem.  I know there's a few threads about people getting black screens when connecting to a remote computer with vnc, but my problem is slightly different.
I use xtightvncviewer on my laptop and tightvncserver on my remote desktop, and I can connect and see the desktop somewhat, but the background, the panels, and some icons are all completely black.  It makes it difficult to do some tasks and see things.

I also don't know why it's not using a gnome desktop when i specified to use gnome in my ~/.vnc/xstartup.  I had recently installed xfce and lxde (even though i uninstalled lxde recently again) and now it only wants to connect to my desktop using xfce.

I'm pretty sure it's me that's doing something wrong. I'm a little new to this, so I'm guessing there's some setting I didn't put in correctly or something else..  anyway, here's my xstartup script:

```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
/etc/X11/Xsession
# startxfce4 &
gnome-session &

```

and this is what i type in the terminal when i try to connect:

```

xtightvncviewer -geometry 1024x768 -depth 32 127.0.0.1:1

```

I'll also include a screenshot so you can all see sort of what it looks like.
btw, I'm using debian lenny on my remote desktop and linux mint 10 on my laptop, if that makes any difference.

---

### Post by sleepee on 2011-01-14
Never mind.  I had to reinstall debian because of another grub problem I had, so I don't have this vnc problem anymore..

---

