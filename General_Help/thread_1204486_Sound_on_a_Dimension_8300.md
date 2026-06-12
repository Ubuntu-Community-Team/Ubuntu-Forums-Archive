---
title: "Sound on a Dimension 8300"
date: 2009-07-04
forum: General Help
---

### Post by lfaraone on 2009-07-04
Hi, I'm having some sound issues. speaker-test gives "ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM dmixer; Playback open error: -17,File exists"

When I set the device to PulseAudio in the Sound prefs and do a test, I hear the tone but it is inturrupted multiple times a second by silence. (it isn't continuous)

Computer has a Dell SoundBlaster card:
```
lfaraone@merlin:~$  cat /proc/asound/cards
 0 [Live           ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0xdf20 irq 17
```

---

