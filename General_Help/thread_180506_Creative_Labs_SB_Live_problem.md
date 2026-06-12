---
title: "Creative Labs SB Live problem"
date: 2006-05-22
forum: General Help
---

### Post by mlorica on 2006-05-22
hello, my sound card is Creative Labs SB Live! EMU10k1 (rev 07)
and i have this error "No volume control elements and/or devices found"

pls. guide me how to configure this on my breezy. thank you

---

### Post by themadhatter0 on 2006-05-22
I had the same problem but it disappeared when I upgraded to Dapper Beta, however if you are not familiar with Linux you might not want to use the beta since it may create other problems. The final release of Dapper should be coming out in the next few weeks so you won't have long to wait if you don't want to tackle the beta version!

---

### Post by silentb on 2006-05-22
My guess is you need a newer version of ALSA. Unfortunately this isn't possible without recompiling the kernel or upgrading to Dapper. Dapper is rather stable though for most people (with one exception: usb printing..). So you might give it a try.

---

### Post by mlorica on 2006-05-22
but it is working a week ago, im using breezy for almost a year, i dont know exactly what happened. pls somebody guide me to edit some configuration files . thank you for your responses.

---

### Post by themadhatter0 on 2006-05-28
so you aren't getting any sound at all now? where is this message appearing?

---

### Post by mlorica on 2006-05-29
i didn't. If I want to use gxine or xmms i have to invoke it from the command line in sudo way "sudo gxine|xmms". but the problem is the quality of sound is not that good as before because it uses the default driver, not my real sound card driver (Creative SB Live) . please help me for some configuration upon boot-up. thanks a lot

---

### Post by Sutekh on 2006-05-29
Can you post the output from this command
```
lspci | grep audio
```
to see what card you have
```
lsmod | grep snd
```
to see what sound modules you have, and if they are appropriate.

---

### Post by mlorica on 2006-05-31
first command:

Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

second :

snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul ,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  1 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,s nd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  13 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_ seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd

---

