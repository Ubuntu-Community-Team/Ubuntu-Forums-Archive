---
title: "PulseAudio or Alsa?"
date: 2010-12-23
forum: General Help
---

### Post by asusx on 2010-12-23
I can't figure out if my laptop is using pulseaudio output or alsa... I'm trying to setup mpd server, but MPC won't play or change the volume. I need to figure out what output should i use in mpd config file. My sound works fine with other applications. And in Mixer settings I have more than one device and some are alsa, some pulseaudio. Any suggestions?

EDIT: Trying to change the volume with 'mpc volume 100" give me 'error: problem setting volume'

---

### Post by Jose Catre-Vandis on 2010-12-23
This should help:

[http://mpd.wikia.com/wiki/Configuration](http://mpd.wikia.com/wiki/Configuration)

Suggests you create an ~/.asoundrc.conf file to point mpd at your sound card. Options for alsa and pulseaudio, I would go for alsa personally.

---

