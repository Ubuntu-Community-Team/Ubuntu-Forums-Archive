---
title: "pSX problem"
date: 2010-08-03
forum: General Help
---

### Post by Mr Nemo on 2010-08-03
Having a little trouble running pSX. I got it to work for about an hour yesterday but now it's coming up with a error i haven't seen before.

```
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Timeout

[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Connection refused'
pSX: ../../../src/pcm/pcm_params.c:2274: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

```

Whats the problem here?

---

### Post by Mr Nemo on 2010-08-04
Also getting (basically the same I think):

```

Home directory /home/eiven not ours.
ALSA lib ../../../src/pcm/pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Device or resource busy'
pSX: ../../../src/pcm/pcm_params.c:2274: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

```

bump

---

