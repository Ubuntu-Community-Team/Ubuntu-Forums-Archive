---
title: "MPD + install help breaks PulseAudio?"
date: 2010-06-26
forum: General Help
---

### Post by liniaal on 2010-06-26
Hi

After i tried a lot of mpd.conf tricks, I followed the tips on [https://help.ubuntu.com/community/MPD]("https://help.ubuntu.com/community/MPD"), namely, adding the mpd user to groups pulse and pulse-access. Now, which makes me really happy, MPD can have audio output. Downside: no other program can make sound, I can't make my beats again with lmms etc. The volume icon in the top right is always on mute, when i click preferences, the hardware tab didn't even show a device. Now it does, but nothing comes out except mpd out - and pressing the volume keys will display a notification but the main icon in the bar stays on "---" mute. Can i make mpd just an application on the pulseaudio outputs list, so that it can play nicely with the other guys?
(of course, tell me any kind of logs you need.)

---

### Post by liniaal on 2010-06-27
and what i just remembered: when i only added mpd to the 2 groups and restarted that service, it was ok, namely mpd could play music i think and also youtube in chromium or whatever. Only when i rebooted it became impossible..

---

