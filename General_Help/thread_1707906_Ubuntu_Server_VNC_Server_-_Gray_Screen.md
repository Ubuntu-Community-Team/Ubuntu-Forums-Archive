---
title: "Ubuntu Server VNC Server - Gray Screen"
date: 2011-03-15
forum: General Help
---

### Post by ondemanddesign on 2011-03-15
I have installed vnc4server

```
sudo aptitude install vnc4server xinetd
```

Then I did:

```
sudo vim ~/.vnc/xstartup
```

And uncommented the top two lines that are recommended to uncomment.

```

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

```

Now when I use a vnc viewer on Windows 7 to view the Ubuntu Desktop I get the following:


Any ideas are appreciated. Thanks.

---

### Post by Azdour on 2011-03-16
Hi,

Change

```
x-window-manager &
```

to

```
gnome-session &
```

My xstartup looks like this:

```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &

```

---

### Post by ondemanddesign on 2011-03-16
That did not work, additionally, when I try to run the server, I get this error:

```
xauth:  error in locking authority file /home/nebula/.Xauthority

New 'Mater:1 (nebula)' desktop is Mater:1

Starting applications specified in /home/nebula/.vnc/xstartup
Log file is /home/nebula/.vnc/Mater:1.log
g
```

Any idea what is going on here?

The Mater:1.log looks like this:

```
 Free Edition 4.1.1 - built Apr  9 2010 15:59:33
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Wed Mar 16 18:28:36 2011
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
exec: 5: /etc/X11/xinit/xinitrc: Permission denied
```

---

### Post by Azdour on 2011-03-17
Hi,

Did you start vncserver using:

```
sudo vncserver
```

Usually the way I use VNC is to log into the machine via ssh as the user. I then run vncserver as that user.

I'm only guessing but when you first ever run vncserver thats when it creates the .Xauthority. If you have run it as sudo its probably owned by root hence the error with locking the file.

---

### Post by ondemanddesign on 2011-03-20
> **Azdour said:**
> Hi,

Did you start vncserver using:

```
sudo vncserver
```

Usually the way I use VNC is to log into the machine via ssh as the user. I then run vncserver as that user.

I'm only guessing but when you first ever run vncserver thats when it creates the .Xauthority. If you have run it as sudo its probably owned by root hence the error with locking the file.

I found the issue, it seems that the permissions on xinitrc were incorrect.

```
exec: 5: /etc/X11/xinit/xinitrc: Permission denied 0
```

I fixed the permissions and it works fine now.

---

