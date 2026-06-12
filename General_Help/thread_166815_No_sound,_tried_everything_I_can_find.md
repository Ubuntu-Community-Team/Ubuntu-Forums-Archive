---
title: "No sound, tried everything I can find"
date: 2006-04-27
forum: General Help
---

### Post by daboochmeister on 2006-04-27
At my wit's end (admittedly, didn't take long :) ...

I have an Ensoniq 1371 card -- seems to be recognized fine by hw detect, lspci shows it, etc.  I did all the ALSA-project recommended config (updated alsa-base file in /etc/modutils, ran sudo update-modules, created ~/.asoundrc, etc.).  I've tried everything described in every thread I could find.  STILL no sound ... unless I unmute "IEC 958 1" in alsamixer -- if I do that, I get a steady static, and if I play e.g. an ogg, very very very quietly I can hear it playing, but extremely quietly, barely hear it.

Any help?  tia

---

### Post by the_burk on 2006-04-27
i think theres a problem with the alsamixer gui.. try man alsamixer and see how to set main volume and pcm volume i dont know the exact command so google it .. but its more or less alsamixer main 100 or alsaconf or somethin like that...

sorry for the fussy answer..

---

### Post by daboochmeister on 2006-04-27
Thx for replying -- I *think* everything is set right, i've used both alsamixer and alsamixergui to set things and both register the same values, plus "amixer scontents" seems to match what I see in the gui (pasted in below).

One thing I was uncertain about -- many of the threads mention running "System -> Properties -> Sound", or running gstreamer-properties, then setting ALSA as the sound engine; I'm running Kubuntu, so this doesn't work.  I assume the equivalent is doing System Settings -> Sound and Multimedia, then setting the "Select the Audio Device" dropdown on the Hardware tab of the Sound System section to ALSA.  I *think* this gets it, because when I run vlc from the command line, msgs such as "alsa audio output warning: recovered from buffer underrun" appear; so it does appear to be using ALSA.

I think I'm going to open another topic to just plain see if there's ANYONE successfully using this card, hoping i can copy their exact config.

amixer scontents returns:

Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 15 [100%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 15 [100%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Line In->Rear Out',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities:
  Mono:
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 24 [77%] [on] Capture [on]
  Front Right: Playback 24 [77%] [on] Capture [on]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [on] Capture [off]
  Front Right: Playback 23 [74%] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities:
  Mono:
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

---

