---
title: "How to fix 8.04 sound issues ?"
date: 2009-10-17
forum: General Help
---

### Post by OpenGuard on 2009-10-17
Ok, basically, after trying out Karmic and seeing that my bug report is still pending approval ( regarding video card driver ), I see no point of replacing my 9.04 with a newer version. What I thought I should do is to install LTS, which means, I will have no need to worry about things that may get ~cherry~ up for an unknown reason ( 8.10, 8.04, 9.04 - works perfectly .. 9.10 suddenly says "stop" ).

Problem: 8.04 supports only 1 audio stream at a time ( by default ), which means, if I'm listening to radio through Audacious and want to open YouTube ( like listening to a tutorial, with some music in background ), I will not be able to do so ( as YouTube will be the second stream ).
Someone suggested me to take a look at ALSA, but as far as I see ( 2.5 hours of pure research ), nothing have been changed .. I still can't listen to more than 1 stream at a time.

Hope you'll get the idea of what's going on here and why I need to switch ( as that's one of the most common questions in such threads ).

Any ideas ?

---

### Post by mikewhatever on 2009-10-17
I'll get straight to the point and skip the BS about cherries and unknown reasons. If memory serves me right, I removed pulseaudio and changed everything in the Sounds window to Alsa in Hardy, and then multiple sound streams worked fine.

---

### Post by OpenGuard on 2009-10-17
> **mikewhatever said:**
> I'll get straight to the point and skip the BS about cherries and unknown reasons. If memory serves me right, I removed pulseaudio and changed everything in the Sounds window to Alsa in Hardy, and then multiple sound streams worked fine.

If the first part seems to be more like a BS than an introduction to why I need this, ok - that's your point of view and I can't / don't want to change it. Regarding puseaudio and alsa - will take a look at it in a few moments and report back as soon as possible.

---

