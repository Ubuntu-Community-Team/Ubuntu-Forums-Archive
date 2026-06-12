---
title: "Dbus in SSH"
date: 2011-10-10
forum: General Help
---

### Post by gwbennett on 2011-10-10
I added "alias pause='dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Pause'" to my ~/.bashrc file

Running pause from a terminal window works fine, but if I try to run it from SSH I get:

"Failed to open connection to "session" message bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed."

Is there a way to make this work?

---

### Post by matt_symes on 2011-10-10
Hi

This is a total shot in the dark but i am wondering if your DISPLAY variable is not set up correctly over ssh.

Over your ssh connection, post back the results of

```
echo $DISPLAY
```

Kind regards

---

### Post by gwbennett on 2011-10-10
echo $DISPLAY merely returned a blank line

---

### Post by matt_symes on 2011-10-11
Hi

> **gwbennett said:**
> echo $DISPLAY merely returned a blank line

I suspect that may be at least part of the problem. I think it does not know which display to connect to.

Try this. Over the ssh connection

```
export DISPLAY=0:0
```Then run your dbus command. Does that get you anywhere ?

BTW: I cannot make head nor tail of your attached thumbnail on ypur first post.

Kind regards

---

