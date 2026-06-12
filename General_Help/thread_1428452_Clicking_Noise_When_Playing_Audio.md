---
title: "Clicking Noise When Playing Audio"
date: 2010-03-12
forum: General Help
---

### Post by Joseph Schwenker on 2010-03-12
I am using Ubuntu 9.10 x64 on an HP Pavillion, p6110y PC.  Whenever I playback audio, and have not played audio for several seconds, I hear a clicking noise before the audio starts to play.  I did not have this problem with Ubuntu 9.04 x64 on the same computer, and I think that PulseAudio is to blame, as usual.  Does anyone have any advice as to how to stop this clicking noise?  I found something that might be relevant to this issue: [http://www.flibblesan.co.uk/2009/10/hd-audio-and-clicking-sound-before-playback-bug/](http://www.flibblesan.co.uk/2009/10/hd-audio-and-clicking-sound-before-playback-bug/).  Thanks!

---

### Post by sandyd on 2010-03-12
```

gksudo gedit /etc/modprobe.d/alsa-base.conf


```
change the last line to
```
 
options snd-hda-intel power_save=0 power_save_controller=N
```

[https://launchpad.net/bugs/442463](https://launchpad.net/bugs/442463)

---

### Post by Joseph Schwenker on 2010-03-12
The click is significantly softer now, barely noticeable.  Thanks!

---

### Post by Joseph Schwenker on 2010-03-12
Actually, I am still getting the sound, although less often.

---

