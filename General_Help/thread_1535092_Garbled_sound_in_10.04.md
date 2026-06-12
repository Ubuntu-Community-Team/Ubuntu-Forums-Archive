---
title: "Garbled sound in 10.04"
date: 2010-07-20
forum: General Help
---

### Post by intheflesh on 2010-07-20
OK, this is a really strange issue I'm having with playing some mp3 files. When using Totem or Rhythmbox, after some time (it may be 10 seconds or a couple of minutes), the sound gets garbled, sped up by approximately 5% and in higher pitch. If I exit the player and play the file again, the problem is gone (until it comes again, not much time from that). That affects audio from some video files.

Also, there is a quick scratchy noise at the very beginning of playback, as well as with sound preview on mouseover in Nautilus.

Other players don't have that issue (SMPlayer, mpg123...)

My PCM volume is not 100% and setting it to lower values doesn't work.

The problems are more noticeable if I do something that uses hard disk (installing software, for example.) They weren't present in 9.04 nor 9.10.

---

### Post by intheflesh on 2010-07-21
It turns out I can fix the issue with **[FONT=Courier New]sudo alsa force-reload[/FONT]**. I don't understand, I chose Pulseaudio as the sound output, why is there alsa running and how does reloading it fix everything?

---

