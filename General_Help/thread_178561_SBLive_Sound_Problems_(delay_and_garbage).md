---
title: "SBLive Sound Problems (delay and garbage)"
date: 2006-05-17
forum: General Help
---

### Post by cjserio on 2006-05-17
Hey,

I have a SBLive with an emu10k chip. I'm using ALSA for both input and output and i'm using the drivers that came with Ubuntu 5.10. Sound works but sounds are very often delayed. If i watch any kind of video at all, the audio never matches the video. If i pause the video, the sound continues for a second or more as the buffer finishes up.

In addition, sometimes i heard a quick blurb of garbage when i get a new instant message on gaim.

Anyone know what the problem could be?

The system is a P4 2.6GHz with 512MB ram and a 120GB harddrive. My video card (not that it matters) is a GeForce 4.

Thanks,
Chris

---

### Post by woedend on 2006-05-18
I had similar issues, and all of this was cured in Dapper for some reason.  As for the delay, are you sure it's not flash based videos?  Flash basically sucks in linux and there is not a good cure for this delay.
But just opening an mpg or avi file it should be synced.

---

### Post by cjserio on 2006-05-18
Hmm actually it is flash based video like Google Video, YouTube etc. So it's a flash problem eh? Well that's annoying but i guess i can live with that.

---

