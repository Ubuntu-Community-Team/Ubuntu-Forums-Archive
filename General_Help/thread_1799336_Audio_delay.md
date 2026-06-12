---
title: "Audio delay"
date: 2011-07-07
forum: General Help
---

### Post by Condor Cluster on 2011-07-07
I've noticed recently that when I play a movie file in vlc, the audio is delayed/out of sync with the video. I can sync them in vlc with the 'j' an 'k' keys, and it always seems I have to set audio to -300ms for it to be in sync.

Has anyone else experienced something like this recently? I'm hoping it's just a vlc thing that will get fixed in the next update...

---

### Post by tigerlxxv on 2011-08-01
vlc doesn't always play nicely with the ALSA interface, and it seems that -300 is about how much delay you get. Make sure VLC is outputting to ALSA and that should fix it, although there are some who report the sound dropping out if you pause it this way. Another workaround is to downgrade to 1.9.1.

---

