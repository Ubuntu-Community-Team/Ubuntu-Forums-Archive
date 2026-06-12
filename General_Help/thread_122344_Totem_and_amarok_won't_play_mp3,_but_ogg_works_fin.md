---
title: "Totem and amarok won't play mp3, but ogg works fine"
date: 2006-01-27
forum: General Help
---

### Post by slashem on 2006-01-27
I suspect some problem with gstreamer??

mplayer and mpg123 play mp3's just fine.

:confused:

---

### Post by Perfect Storm on 2006-01-27
enable universe and multiverse in your sourcelist.

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-plugins-multiverse
gst-register-0.8

```

---

### Post by slashem on 2006-01-27
Thank you, that did the trick :)

---

### Post by lorap on 2006-01-27
hi friend,
try do instal via synaptic all gstreamer plugins available.
it fixed the same problem at my pc.

---

### Post by nrwilk on 2006-02-22
I found that Amarok works much better for me with the xine engine.  Installing Amarok-xine in synaptic fixed the mp3 issue, and also fixed my issue with Amarok where it couldn't play streaming internet audio.

If you do this, remember that you need to select the new engine under Amarok too, in it's preferences.

---

