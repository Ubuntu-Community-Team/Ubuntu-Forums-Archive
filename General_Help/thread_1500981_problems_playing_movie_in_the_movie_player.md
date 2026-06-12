---
title: "problems playing movie in the movie player"
date: 2010-06-03
forum: General Help
---

### Post by hunterkasy on 2010-06-03
I have Ubuntu 10.04 with the latest updates, I am trying to play an mkv avi movie with the default movie player: Totem Movie Player 2.30.2 The movie plays just fine with good audio and video, and it plays for about 3-4 minutes then the player just closes down back to the desktop, with no messages of any kind, I have tried playing the movie several times it does the same thing, after 3-4 minutes the player just closes down,

any idea's on what to Do? Or if their is a better video player that will work?

---

### Post by kerry_s on 2010-06-03
totem is okay, but there are better options. i still keep it as a backup.
i use gnome-mplayer & cache 75% for smooth playback.

```
 -lavdopts skiploopfilter=all -cache-min 75
```

---

### Post by hunterkasy on 2010-06-03
> **kerry_s said:**
> totem is okay, but there are better options. i still keep it as a backup.
i use gnome-mplayer & cache 75% for smooth playback.

```
 -lavdopts skiploopfilter=all -cache-min 75
```

I installed gnome-mplayer and put in: -lavdopts skiploopfilter=all -cache-min 75, in the right spot and now the movie plays like it suppose to thanks for your help

---

### Post by lovinglinux on 2010-06-03
> **hunterkasy said:**
> I installed gnome-mplayer and put in: -lavdopts skiploopfilter=all -cache-min 75, in the right spot and now the movie plays like it suppose to thanks for your help

I like gnome-mplayer and the corresponding plugin, [gecko-mediaplayer](apt:gecko-mediaplayer), which I highly recommend. Nevertheless, my main standalone player is [smplayer](apt:smplayer).

---

