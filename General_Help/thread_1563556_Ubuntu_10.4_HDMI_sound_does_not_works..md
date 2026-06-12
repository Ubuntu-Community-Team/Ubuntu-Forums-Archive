---
title: "Ubuntu 10.4 HDMI sound does not works."
date: 2010-08-29
forum: General Help
---

### Post by Diogo Falcomer on 2010-08-29
So guys, today I put a hdmi cable on my note, I turned on the TV and ran to
is a beauty but when I turned on the video ... the sound did not come.

I went to System -> Preferences -> Sound and changed the output to "Digital Stereo
(HDMI) output. And no sound came out. The boxes of note works perfectly.

Has anyone had this problem?

Here follows some details of the hardware:

```
$ aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 3: INTEL HDMI [INTEL HDMI]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
```

```


snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25677  2 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71106  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm


```

---

### Post by Diogo Falcomer on 2010-08-30
up!

---

### Post by hackob on 2010-09-01
I'm having the same problem with HP dv5, any one having the same problem or a solution?

---

