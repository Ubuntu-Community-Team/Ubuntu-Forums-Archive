---
title: "Audio Transport Development Project"
date: 2010-09-22
forum: General Help
---

### Post by GaryH on 2010-09-22
Hi Everybody,

I'm running 10.04 and what to send/get audio samples to/from my sound card. Is the ALSA api the way to go? Is there a better (more modern) way to go? I noticed asoundlib.h header file was absent from 10.04 but the ALSA library was present. I'm worried that the header file's absence is a bad sign. I built a small tutorial program just to check out the build environment and noticed a warning in pcm.h. Is this a bad sign? 

> [INDENT]warning: /usr/include/alsa/pcm.h:622: note: expected ‘unsigned int *’ but argument is of type ‘int’[/INDENT]

It appears pulseAudio rides on top of ALSA. Correct? What the heck is JACK? Should I study up on it?

Any advice will be most welcome:guitar:

Many kind thanks,
GaryH

---

