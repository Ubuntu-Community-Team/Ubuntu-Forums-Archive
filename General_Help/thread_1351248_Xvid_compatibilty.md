---
title: "Xvid compatibilty?"
date: 2009-12-10
forum: General Help
---

### Post by rahilm on 2009-12-10
Does Ubuntu play xvid files out of the box like ogg or ogv??
I ask this because i came to know that xvid is opensource under GPL.
I can't test this because i don't have any xvid files to work with and i have polluted my ubuntu with gstreamer to check if it works OOTB.

---

### Post by mc4man on 2009-12-10
> Does Ubuntu play xvid files out of the box like ogg or ogv??

No

libavcodec would need to be installed,  which it isn't by default.

The min for totem would be the gstreamer0.10-ffmpeg plugin and depending on audio stream probably the gstreamer0.10-plugins-ugly

A third party player like vlc or mplayer could playback after installing

---

### Post by rahilm on 2009-12-10
> **mc4man said:**
> No

libavcodec would need to be installed,  which it isn't by default.

The min for totem would be the gstreamer0.10-ffmpeg plugin and depending on audio stream probably the gstreamer0.10-plugins-ugly

A third party player like vlc or mplayer could playback after installing


In my Opinion, it should support xvid ootb, since it being open source and all.

---

### Post by rahilm on 2009-12-10
maybe this is not the right section of the forum to talk about it

---

