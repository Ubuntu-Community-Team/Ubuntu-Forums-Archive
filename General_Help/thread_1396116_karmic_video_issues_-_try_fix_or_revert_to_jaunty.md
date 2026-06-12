---
title: "karmic video issues - try fix or revert to jaunty"
date: 2010-02-01
forum: General Help
---

### Post by pickarooney on 2010-02-01
I installed karmic about two weeks ago and have been having all manner of video problems. At this stage I think I should just reformat and install jaunty again on both my PCs. I'd ideally like to fix the karmic problems but I'm beginning to think these are chronic bugs and there's no reasonable way to fix them.

 - video playback in smplayer is dodgy. after a while the image will stop and/or go really fast and jerky
 - youtube videos in firefox behave in a similar manner
 - I get a freaky big black cursor flashing all over some websites
 - random screen-pukes. the screen becomes filled up with bits and pieces of hundreds of windows (very hard to describe accurately)
 - tv tuner no longer works
 - webcam no longer works
 - on the laptop it's impossible to get the nvidia drivers to display anything on the screen


Now, maybe I just need to find a better set of drivers (I'm using nvidia version 185), but I'm not convinced.

Does this set of issues appear to have a common theme otherwise or has anyoen had most/all this crap with karmic andhow have you resolved it?

---

### Post by rvm4000 on 2010-02-01
> **pickarooney said:**
>  - video playback in smplayer is dodgy. after a while the image will stop and/or go really fast and jerky

Change the audio driver from alsa to pulse in preferences -> general -> audio.

---

### Post by pickarooney on 2010-02-02
> **rvm4000 said:**
> Change the audio driver from alsa to pulse in preferences -> general -> audio.

That didn't fix it unfortunately.

---

### Post by pickarooney on 2010-02-02
It looks like my gfx card or drivers are screwed at this stage. What's a safe way to switch to another version of the nvidia drivers?

---

### Post by pickarooney on 2010-02-02
Older drivers don't display any image when playing video, so that was a failure.
Now I need to figure out how to enable my on board gfx card and use it as default.

---

### Post by pickarooney on 2010-02-02
Enabled my onboard ATI card and ran envyng to install the ATi drivers, but got an Out of Synch error when X tried to load. Switched to 'ati' in the xorg.conf and ended up with a really slow, crappy driver.

Is there some simple way of enabling the fglrx driver so I can test if my problems stem from the hardware, software, drivers or OS?

---

