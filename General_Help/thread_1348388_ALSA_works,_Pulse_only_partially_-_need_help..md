---
title: "ALSA works, Pulse only partially - need help."
date: 2009-12-07
forum: General Help
---

### Post by endBc on 2009-12-07
[[IMG]http://img11.imageshack.us/img11/7130/200912071320381280x1024.th.png[/IMG]]("http://img11.imageshack.us/i/200912071320381280x1024.png/")

Audacious and VLC volume - 100%. 
Why only one of them ( VLC ) hits the 100% mark ? Audacious is way too silent and I can't get it louder without redirecting it's output to ALSA which is not a solution because when I pull the volume down, the whole PCs volume goes down too.

Any ideas ?

---

### Post by endBc on 2009-12-07
[color=gray][ --- ][/color]

---

### Post by endBc on 2009-12-09
Hopeless bump ..

---

### Post by Dr. Oddbio on 2009-12-09
I can't see the image.

---

### Post by endBc on 2009-12-09
> **Dr. Oddbio said:**
> I can't see the image.

Didn't even noticed it - worked when I uploaded it. Basically, all it shows is VLC which hits the 100% and Audacious which barely gets to the 60% mark. Why it is so ?

---

### Post by Dr. Oddbio on 2009-12-09
no idea.
I'm actually having trouble with audio myself which is why I found this thread.

---

### Post by jocko on 2009-12-09
It's probably the "Replay Gain" function in audacious that reduces the output volume to prevent clipping (~distortion when something tries to play at more than 100%).
You can fix this either by activating "Bypass all of signal processing if possible" in the "audio" tab in audacious preferences, or by increasing "Default gain" in the replay gain configuration, or by inactivating replay gain completely (this may cause distorted sound on files that are recorded or encoded with too high volume, but should be fine for good quality files).

---

