---
title: "Maverick display / computer sleep despite being set to never."
date: 2010-10-20
forum: General Help
---

### Post by roganjosh on 2010-10-20
Hi.

I applied Power Management settings to put my computer to sleep in the hope that it would only sleep when it wasn't downloading something in Deluge. Unfortunately it would seem that it puts the computer to sleep despite Deluge being active. No biggie I thought, I'll just disable the sleep settings my setting them both back to NEVER. However, it ignores my new settings and still puts the display / computer to sleep, at the exact times I set originally!

Any way around this?

---

### Post by woeskwee on 2010-10-24
I had a similar problem that turned out to be my screensaver.  I got excellent advice instantly on irc.ubuntu.com using pidgin.  channel #ubuntu is advice for relative beginners.  My problem was the screen going blank after 5 min, but I would not loose sound.  I set my screensaver to a longer time and unchecked the lock screen whenever screensaver is active box, so I wouldn't have to keep entering my password.

---

### Post by roganjosh on 2010-10-25
Thanks, my screensaver isn't set to active though :(

---

### Post by cariboo on 2010-10-25
Have you changed the settings in System->Preferences->Power Management? By default it's set for 15 minutes.

---

### Post by roganjosh on 2010-11-09
Nope, everything is set to never :(

---

### Post by plucky on 2010-11-09
> **roganjosh said:**
> Nope, everything is set to never :(

Check your BIOS settings for power saving modes.

---

### Post by roganjosh on 2010-11-10
> **plucky said:**
> Check your BIOS settings for power saving modes.

Had a look at this and the only enabled setting was something to do with enabling deep power off or something. Anyway I disabled that and I'm still having the same problem. Strange thing is that it was staying awake before I set a suspend time, and it changed OK when I set one, but now that I've set it back to never it just seems stuck on the time I set it on beforehand.

EDIT: I'm potentially an idiot. I've been leaving XBMC running fullscreen, which I've just noticed has it's own suspend settings. I've set those to never now so I'll see if that fixes it, which looks likely!

---

### Post by roganjosh on 2010-11-15
Yep. I was an idiot... This is now fixed :\

---

