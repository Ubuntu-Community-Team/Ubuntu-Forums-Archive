---
title: "Kaffeine-xine crackly sound"
date: 2006-02-06
forum: General Help
---

### Post by Michel F on 2006-02-06
I installed kaffeine-xine on Kubuntu 5.10 and selected xine-engine.

Whenever I launch Kaffeine left-clicking a videofile, the sound produced is crackly. I tested that on several file types (avi, mpeg and also quicktime, wma).

What's strange is that if I open the configure menu / confgure engine and audio tab, if I select the audio output choice (set by default to "default"), even if I change NOTHING, but simply touch this field and exit from configuration, then the sound becomes good. It also become good if I select alsa.

But the sound will be ugly again if I exit kaffeine and launch it again, whatever choice I did select in the configuration.

Any similar experience ? Any solution ?

---

### Post by Michel F on 2006-02-06
OK found a solution. In the Xine engine configuration menu, there's a tab at the bottom (Misc). I checked the "apply implicit changes" option. Seems to be enough.

---

