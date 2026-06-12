---
title: "Trouble Setting VLC Volume From Command Line With DBUS"
date: 2012-09-06
forum: General Help
---

### Post by hwttdz on 2012-09-06
I'm having trouble setting the vlc volume from the command line using DBUS.  I can fetch the volume using:

> qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Volume
1.34765625

But if I try to add a value for instance "1.34765625" the volume is set to zero

> qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Volume 1.34765625
> qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Volume
0

Thoughts?

---

