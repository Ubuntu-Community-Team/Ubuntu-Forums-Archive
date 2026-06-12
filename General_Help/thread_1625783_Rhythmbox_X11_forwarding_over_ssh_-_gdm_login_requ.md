---
title: "Rhythmbox X11 forwarding over ssh - gdm login required"
date: 2010-11-19
forum: General Help
---

### Post by gdebat on 2010-11-19
I want to play music on my netbook (UNR 10.04) controlling it from a remote machine (Karmic). So far I have managed to do so by using X11 forwarding to fire up rhythmbox however I need to log in at the GDM login screen on the netbook in order to hear anything. I've tried to add the user to the pulse and pulse-access groups (on the netbook of course) but that did not solve anything. The only work-around I've found was to use auto-login but I would like to know if there is an alternative way to use rhythmbox without having to log in.

PS. I'm not considering music server solutions (xmms2, mpd) as I've made up my mind about using Rhythmbox over X11 ssh forwarding.

---

### Post by gdebat on 2010-11-20
Anyone? At least can someone confirm that this 'limitation' exists not just on my configuration?

pretty please ;)

---

### Post by gdebat on 2010-11-20
[SOLVED]

Tried mpg123 to see if without any X forwarding my netbook could play music but it did not. So...

On the netbook I added my user to the audio, pulse and pulse-access groups. Don't know which one(s) were really required, will check later on... but with all three, I'm happy listening to my music collection, controlling it remotely... damn that feels good lol

---

### Post by tredegar on 2010-11-20
I think you need to be logged in before rhythmbox can access the sound device.

Maybe run a gnome session on the netbook with **vncserver** and connect to that?

The extra packages you'll need are **xvnc4viewer** and **vnc4server**

To start the server, login to the netbook as yourself, then you need this file on your netbook **/home/gdebat/.vnc/xstartup** and it should contain:
```
#!/bin/sh
unset DBUS_SESSION_BUS_ADDRESS
gnome-session &
```
Now start the server on the netbook:
```
vncserver :1 -geometry 1024x768 -depth 24
```

Connect to it from your karmic machine:
```
vncviewer netbook:1
```
If you don't like the terminal, there's **remmina** that'll connect to the netbook, with clicky-clicky in the GUI.

Start rhythmbox on the netbook by the usual process, but you are doing it from your karmic machine, using the viewer.

All should be good. If you disconnect your viewer, the netbook will continue to play music because the process is still running. You can reconnect to it later.

To start the vncserver at every boot, in **/etc/rc.local** (on the line before the final **exit 0** ) put
```
su - gdebat -c " cd /home/gdebat/ && vncserver :1 -geometry 1024x768 -depth 24 "
```

---

### Post by tredegar on 2010-11-20
We cross-posted, but it looks like you solved it.
I type too slowly.

---

### Post by gdebat on 2010-11-21
Thanks for the suggestion anyway, though I would prefer NXServer as it's more configurable and generally more responsive than vnc... and it uses X forwarding so I can just fire up a single application as opposed to a whole remote desktop.

---

