---
title: "Audio volume very high on startup"
date: 2012-01-14
forum: General Help
---

### Post by ubiquitin.jf on 2012-01-14
I've been experiencing a rather peculiar bug for about 4 months now. Ubuntu does not remember the audio volume set last session and sets the volume to 80% every time I switch my PC on. I'm getting a little tired of changing my underwear every time I forget about this; does anyone know what's going on? Audio is HDMI out.

---

### Post by xc3RnbFO8P on 2012-01-14
Here is a bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/204536]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/204536")

---

### Post by ubiquitin.jf on 2012-01-14
Well that's annoying. I guess I better stock up on clean underwear then.

---

### Post by pqwoerituytrueiwoq on 2012-01-14
you could replace your login sound in System -> Preferences -> Startup Applications with a script like this:
```
#!/bin/sh
pacmd set-sink-volume 0 3500
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
exit
```

---

### Post by xc3RnbFO8P on 2012-01-14
Just use night pot :)

---

