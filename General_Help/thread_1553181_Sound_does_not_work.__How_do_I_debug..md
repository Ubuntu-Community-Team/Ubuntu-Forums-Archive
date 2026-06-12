---
title: "Sound does not work.  How do I debug."
date: 2010-08-14
forum: General Help
---

### Post by tc101 on 2010-08-14
I am running 10.04 on an old computer.  I can watch netflix videos, but there is no sound.  I tested the speakers on another computer and they work.  That leaves either the sound card, or something about 10.04.  How do I debug this?

---

### Post by murphycc on 2010-08-14
Did you try running 'alsamixer' in your terminal? Make sure the sound levels are not muted. That's exactly the problem I had a while back.

For some reason, my laptop sound was completely disabled at installation and I didn't even know about running alsamixer.

-Chris

---

### Post by tc101 on 2010-08-14
Thanks Chris, you pointed me in the right direction.  I did a search and found the following:

This solved my problem

[https://wiki.ubuntu.com/Audio/CheckForMutedSpeakerVolume](https://wiki.ubuntu.com/Audio/CheckForMutedSpeakerVolume)

And here is a more general process for debugging sound

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

