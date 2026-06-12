---
title: "Sound control not working on Center speaker"
date: 2010-12-20
forum: General Help
---

### Post by NertSkull on 2010-12-20
I am running 10.10.  If I use the volume control on the panel or the pulseaduio volume control to raise/lower the volume, it will raise or lower the volume on my left and right speakers.  But my center speaker (which is plugged into its own port on my motherboard) does not change at all.  It stays the same volume.

Is there something I can do to make all the speakers get controlled by the volume control?  Its weird to me that the side speakers work, but not the center (well it "works" and makes noise, just can't be controlled)

I hope that made sense.

---

### Post by TeoBigusGeekus on 2010-12-20
Open terminal and give
```
alsamixer
```
Make all your changes from there.

---

### Post by NertSkull on 2010-12-20
Well I looked into that, but that doesn't really solve the problem.  Because then I have to turn down the "front" and "center" independently.

I guess in general this wouldn't be a huge deal, except when watching tv/movies I can't use the control really.  Because it will only lower the "front" channels and not the center.

Also I have noticed that the volume control on the panel (and pulseaudio) will lower the volume on the "front" channel from 100-20%.  But the last 20% will then lower the rest of the front and also lower the center channel really fast.

This is not the way it worked in 10.04.  The volume control would lower both.  Its not very useful to have loud volume, try to lower it through the panel, and have it effectively stay the same because the center channel doesn't get any less.

---

### Post by NertSkull on 2010-12-20
I added a couple of screen shots to try to explain what I meant about the controlling front and center at different levels.

---

