---
title: "Gstreamer through Jack not working"
date: 2012-02-23
forum: General Help
---

### Post by M@s on 2012-02-23
Hi,

I've installed the Jack plugin for Gstreamer according to this guide: [http://jackaudio.org/gstreamer_via_jack](http://jackaudio.org/gstreamer_via_jack)

It is working when running sound test signals from gstreamer-properties, but when I launch Banshee and try to play a song, nothing happens and I get this output:
```
[Error 12:49:36.491] GStreamer resource error: NotFound
```

I'm running Ubuntu 11.10 64-bit, how do I proceed?

---

### Post by Gremlinzzz on 2012-02-23
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

sudo apt-get install ubuntu-restricted-extras

---

### Post by Gremlinzzz on 2012-02-23
> **Gremlinzzz said:**
> [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

sudo apt-get install ubuntu-restricted-extras

sudo apt-get build-dep banshee
:popcorn:

---

### Post by M@s on 2012-02-23
Run the commands but no change, I get the same error...

---

### Post by M@s on 2012-02-23
Maybe something gets corrupted when I start Jack. Usually all the non-jack sound is supposed to resume again when Jack is stopped, but this never happens in my case. When I stop Jack, no media applications works and there is no Sound Interface showing up in Sound Properties. Login/out does fix the problem; I have to reboot to get the audio working again.

---

