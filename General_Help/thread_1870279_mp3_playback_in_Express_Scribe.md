---
title: "mp3 playback in Express Scribe"
date: 2011-10-27
forum: General Help
---

### Post by chichiri47 on 2011-10-27
Running  Xubuntu 11.10 on an AMD64; will be happy to provide any other  information, but you'll probably have to tell me how to obtain it.

The native Linux version of NCH Express Scribe -- a program I HAVE to  use for my work, as I cannot find an alternative, and cannot install  Windows on this machine -- is offering me three options for Sound  Device.

(Default Sound Out) uses I'm not sure what, but when I play an MP3 file,  it skips to the last second or so of the file, no matter where I set  the slider. The terminal displays a message every time I manipulate the  audio slider:

     ```

     ALSA lib ../../../src/pcm/pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card 

```
"HDA NVidia: ALC883 Analog (hw:0,0)" plays the audio well enough,  but it skips the audio four seconds forward every time I press the play  button. Four seconds exactly. Every time. And when I hit the rewind or  fast forward buttons, it jumps many, many seconds back or forth. This  makes it useless for transcription work.

Finally, "HDA NVidia: ALC883 Digital (hw:0,1)" does the same thing as above, except without the actual sound.

Under the volume mixer, the options I have for playback are "HDA Nvidia  (Alsa mixer)" and "Playback: Internal Audio Analog Stereo (PulseAudio  Mixer)". As I said, if you tell me how, I'm happy to give any other info  needed.

And before you ask, yes Express Scribe does run well under wine, but the  text entry is sluggish -- if I type really fast (which I often do) I  can't see what I'm typing until after I'm done, and the audio hotkeys  don't work systemwide. I'd be happy to run it in wine if one of these  problems could be solved, so bonus problem, yay!

TIA, everyone. I really hope I can get back to work soon.

---

### Post by chichiri47 on 2011-10-27
bump for great hopefulness

---

### Post by chichiri47 on 2011-10-27
bump for great desperation

---

### Post by chichiri47 on 2011-10-30
Bump. Still need help. :(

---

### Post by Rodney9 on 2011-10-30
Sorry I don't have an answer, but you could look here -
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

