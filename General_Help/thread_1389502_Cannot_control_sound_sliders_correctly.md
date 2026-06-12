---
title: "Cannot control sound sliders correctly"
date: 2010-01-24
forum: General Help
---

### Post by Firestorm21 on 2010-01-24
I'm trying to multiple volume channels using the multimedia keyboard buttons on my laptop. 

I've tried using gconf-editor and editing 
desktop/gnome/sound/default_mixer_tracks 
to include the Master and LFE tracks. This worked when I ran Arch (I didn't have pulseaudio then).

I have edited /etc/pulse/default.pa and added the 
```
load-module module-alsa-sink control=PCM
```
line. I can control either Master, PCM, or LFE with it, but not more than one. Using "control=Master,LFE" doesn't work. "control=Master LFE" doesn't work. "control=[Master,LFE]" doesn't work either.

I'm seriously out of ideas on how to fix the problem. Right now I have it controlling PCM just because that is the only channel that will change the entire volume at the moment, but it won't allow me to mute..

Pulseaudio is a bit crackly when changing the volume sometimes and I'm not sure what the issue with that is either.

---

