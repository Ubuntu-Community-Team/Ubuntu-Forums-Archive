---
title: "Sound suddenly disappeared"
date: 2011-09-12
forum: General Help
---

### Post by NilPointer on 2011-09-12
Everything was OK, but few minutes earlier, audio system stopped. Restarting ALSA and rebooting PC didn't helped.

I've attached two images:

First shows sound icon. Second shows sound icon when attempting to play some files. It turns red.

How to fix it? Thanks in advance!

---

### Post by sanderd17 on 2011-09-12
can you play music with mplayer and see if you get any errors?

(mplayer is a command line tool, just execute "mplayer name-of-music-file")

---

### Post by NilPointer on 2011-09-12
No errors. It starts "playing", however no sound can be heard.

```
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  33.1 (33.1) of 63.0 (01:03.0)  0.8% 

```

---

### Post by sanderd17 on 2011-09-12
hmmm,

Ubuntu doesn't use ALSA anymore. Can you try restarting pulseaudio?

---

### Post by NilPointer on 2011-09-12
Well, after restarting pulseaudio, sound works again now.

Strange, however... After reboot, pulseaudio should be restarted too, right? But it didn't worked...

Anyway, problem solved. Even after reboot, sound doesn't disappear. Thank you very much!

---

### Post by sanderd17 on 2011-09-12
There are happening weird things.

A week ago, my computer booted up very slowly because udev was spitting errors. I saw no way to fix it, until I found a post that I should unplug the power from the computer (it's a desktop, no laptop). I did it, and now udev doesn't spit any errors anymore.

---

