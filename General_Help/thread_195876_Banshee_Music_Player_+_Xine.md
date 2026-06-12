---
title: "Banshee Music Player + Xine?"
date: 2006-06-13
forum: General Help
---

### Post by ubu-for on 2006-06-13
Is it possible to use Xine instead of Gstreamer?

THX!

P.S. Gstreamer doesn't work correctly.

---

### Post by mlind on 2006-06-13
I reckon answer for this is no, it's gstreamer only. If your after xine backend,
how about amaroK ?

btw. What's wrong with gstreamer?

---

### Post by ubu-for on 2006-06-13
[QUOTE=mlind]
how about amaroK ?[/QUOTE]

It's ok, but not my favorite.

[QUOTE=mlind]
btw. What's wrong with gstreamer?[/QUOTE]

MP3 and OGG files get interrupted every 3 seconds. :(

---

### Post by mlind on 2006-06-13
[QUOTE=ubu-for]
MP3 and OGG files get interrupted every 3 seconds. :([/QUOTE]

Do you get same behaviour when playing through gstreamer using command-line?
```

gst-launch filesrc location=my_music_file.mp3 ! decodebin ! audioconvert ! audioresample ! alsasink

```

---

### Post by ubu-for on 2006-06-13
[QUOTE=mlind]Do you get same behaviour when playing through gstreamer using command-line?
```

gst-launch filesrc location=my_music_file.mp3 ! decodebin ! audioconvert ! audioresample ! alsasink

```[/QUOTE]

```

bash: gst-launch: command not found
```

---

### Post by ubnoobie on 2006-06-13
[QUOTE=ubu-for]```

bash: gst-launch: command not found
```[/QUOTE]
gst-launch is in gstreamer-tools

---

### Post by Heliologue on 2007-12-13
I hate to resurrect an old thread, but I feel I should point out, for posterity, that there _is_ a xine backend for Banshee, however unofficial.

[http://i-nz.net/projects/banshee/](http://i-nz.net/projects/banshee/)

---

