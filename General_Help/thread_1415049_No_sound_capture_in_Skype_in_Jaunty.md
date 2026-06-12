---
title: "No sound capture in Skype in Jaunty"
date: 2010-02-24
forum: General Help
---

### Post by Cubytus on 2010-02-24
Hi to all, 

I have trouble using Skype 2.1.0.47. I can hear the answering machine on the other end, but recording sound only gives out static. Skype can only use Pulse Audio server

Sound setttings:
Audio conference is set, for sound playback, at "automatic detection" (all other settings are "Automatic detection"). Capture is at 82801BA-ICH2 with AD1885 Intel 82801BA-ICH2 (ALSA). I tried changing that to OSS, then PulseAudio, but I only get static.

What can I do about that?

---

### Post by gradinaruvasile on 2010-02-24
Skype can use ALSA or PulseAudio just fine depending which one is available.
try the echo test service to see if there is a recording problem. In PulseAudio open the right-click menu from the volume icon from the tray, and see if there is captured sound on the mic level indicator.

If there isnt, you have to open alsamixer in a terminal and go to the recording view (tab changes views) and see the microphone levels and if there is a capture device set - left/right changes the items, up/down the volumes, space toggles the recording device (the latter only available on the devices that have ---- under the volume indicator).

---

