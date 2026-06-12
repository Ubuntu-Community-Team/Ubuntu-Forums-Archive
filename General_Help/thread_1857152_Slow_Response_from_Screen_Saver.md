---
title: "Slow Response from Screen Saver"
date: 2011-10-09
forum: General Help
---

### Post by 9a8sy on 2011-10-09
I'm running version 11.04 on a laptop with a duo core CPU and 2 Gig Ram. Typically with a browser open and a couple minor programs I use about 50% of my ram. If I leave and come back to find my screen saver enabled, it will take several minutes to get my desktop back. During this time it appears I've got a lot of HD thrashing going on and when I do get the desktop back and look at the system monitor, it appears that during screen saver I use 100% of ram. I'm not sure why this is happening but would like some advice as to how I can prevent this from happening.

---

### Post by papibe on 2011-10-09
What screensaver are you using?

Try testing something basic like 'Black Screen'. My first guess is that you are running a screen server that needs video hardware acceleration, OpenGL or something like that. If your computer don't support that, it maybe doing all the work with the CPU, thus the slowness.

Tell us how it goes.
Regards.

---

### Post by 9a8sy on 2011-10-09
Well that appears to have fixed it. Glad it was something easy. Thanks!

---

### Post by papibe on 2011-10-09
:) Glad it's solved. Please mark the thread solved when you have the chance.

---

