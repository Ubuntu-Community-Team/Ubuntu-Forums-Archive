---
title: "Using dd to convert multiple audio files"
date: 2011-01-18
forum: General Help
---

### Post by jmacgowan on 2011-01-18
I have been using the command line program dd to convert music extracted from my iPod from .m4a to .ogg format.

It is working like a dream, but it's extremely tedious.

Is there a way to automate the process a bit?  I could just use another program of course, but where's the fun in that?

---

### Post by dabl on 2011-01-18
ffmpeg works pretty well for that kind of thing.  GUI front ends include the popular winff, as well as audio-convert (using zenity).

---

### Post by psusi on 2011-01-18
> **jmacgowan said:**
> I have been using the command line program dd to convert music extracted from my iPod from .m4a to .ogg format.

It is working like a dream, but it's extremely tedious.


This does not make sense.  dd stands for disk duplicate.  It just copies from a source to a destination.  It has no idea what ogg or m4a are, or any other audio format.

---

