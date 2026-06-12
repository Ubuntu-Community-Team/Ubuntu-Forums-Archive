---
title: "Weird sound problem"
date: 2012-03-19
forum: General Help
---

### Post by kkelly77 on 2012-03-19
If I'm listening to music, on Rhythmbox for example, and I want to watch a YouTube video, I can't hear the sound until I close the other application that is currently producing sound.

This problem applies to any application I use whereby I need to hear the sound from something else. Anyone have any ideas what could be causing this? I haven't changed any settings. Thanks. :guitar:

---

### Post by HiImTye on 2012-03-19
what version of Ubuntu are you using?
if you are using any recent version (i.e. 11.04, 11.10) then try entering:
```
pulseaudio --start &
```
into a terminal

---

### Post by kkelly77 on 2012-03-19
Sorry, should have said

10.04

---

### Post by HiImTye on 2012-03-19
yeah, it should use PulseAudio by default (I believe it's been default since like 8.04 or something) try to start the PulseAudio sound server using 'pulseaudio --start' and seeing if you can get sound from multiple apps. if not, you might give OSS4 a try (or maybe Dmix if you want to spend the time to set it up)

---

### Post by kkelly77 on 2012-03-19
No luck.

Have something playing in VLC and tried to watch a YouTube vid. No sound from the YouTube video while I had VLC paused.

---

### Post by HiImTye on 2012-03-19
try redirecting flash to pulse
make an empty file in your home folder called .asoundrc and paste this into it:
```
#grab everything and direct to pulseaudio
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

---

### Post by kkelly77 on 2012-03-19
> **HiImTye said:**
> try redirecting flash to pulse
make an empty file in your home folder called .asoundrc and paste this into it:
```
#grab everything and direct to pulseaudio
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

Should I reboot after I create the file?

---

### Post by HiImTye on 2012-03-19
you shouldnt need to, .asoundrc is accessed every time an ALSA app loads

---

### Post by kkelly77 on 2012-03-19
> **HiImTye said:**
> you shouldnt need to, .asoundrc is accessed every time an ALSA app loads

Oh OK. 
Still no joy.

---

