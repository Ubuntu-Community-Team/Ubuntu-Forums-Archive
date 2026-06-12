---
title: "Improper Sound in Games"
date: 2009-11-11
forum: General Help
---

### Post by Unanimated on 2009-11-11
When I play OpenArena, all of the sound sounds like static, which didn't happen in 9.04 (I'm running 9.10.). When I play Unreal Tournament 2004, the sound works if I'm not running a music player but breaks it when I close it (I have to do a full restart of the computer to get it working properly again) and there is no sound if I *am* playing music. In Tremulous, the sound is completely fine. Is there a connection between OA and UT2004? And how can I fix this?

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
If you're running pulseaudio then you can restart it with "pulseaudio -k" instead of rebooting. You might want to make sure you have the alsa plugins for pulseaudio. This [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) may help.

---

