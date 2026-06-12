---
title: "vnc xstartup file"
date: 2012-07-31
forum: General Help
---

### Post by spunkycabage11 on 2012-07-31
Whenever i try to vnc into my server I get a grey screen with a x for a cursor and 3 checkboxes.

I'm running Ubuntu 12.04

I'm pretty sure it has something to do with my startup file, can someone tell me what's wrong with it?
Here's my startup file:

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
#exec /etc/X11/xinit/xinitrc
gnome-session -session=gnome-classic& 

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &

```

Thanks in advance

---

### Post by Toz on 2012-08-06
See [here]("http://ubuntuforums.org/showthread.php?t=2038352") - situations look very similar.

---

