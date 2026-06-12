---
title: "a VNC rejects DockbarX"
date: 2011-03-19
forum: General Help
---

### Post by saltcushy on 2011-03-19
My all servers VNC rejecting DockbarX, probably lack something  of xstartup, right?
```
#!/bin/sh
# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &

```

---

