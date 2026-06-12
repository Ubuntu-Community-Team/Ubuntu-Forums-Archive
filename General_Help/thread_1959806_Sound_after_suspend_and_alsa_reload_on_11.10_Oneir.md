---
title: "Sound after suspend and alsa reload on 11.10 Oneiric"
date: 2012-04-16
forum: General Help
---

### Post by serafin on 2012-04-16
I have an old Dell Dimension 4550 computer with a Creative Labs [SB Live! Value] EMU10k1X sound card, and sound after suspend has never worked for me (no sound whatsoever after suspend). However, on previous distributions I could always restart/reload alsa and I would have sound again. However, on Oneiric, the command

```
sudo alsa force-reload
```

yields the output

```
Unloading ALSA sound driver modules: snd-emu10k1x snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-emu10k1x snd-ac97-codec snd-pcm snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-emu10k1x snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
```

So, some modules seem to fail to unload. What's wrong and what can I do about it?

---

