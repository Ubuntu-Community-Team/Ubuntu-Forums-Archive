---
title: "Ubuntu 'Breezy' - Alsa / Audigy sound card problems... please help!"
date: 2006-05-09
forum: General Help
---

### Post by Duke_Of_Earl on 2006-05-09
Hi all,

I'm totally new to Linux (installed Ubuntu about a week ago) but have managed to slog my way into a functional system except for one thing - sound.

I have a Creative Labs Audigy 2 Value sound card with 5.1 surround speakers but cannot hear anything under Ubuntu 5.10 'Breezy' (Kernel 2.6.12-10-386).  Works fine in Windoze XP.

I have tried the sound card HOWTO here along with many other tips and tricks I've found on Google to no avail. I'm hoping that someone here can help me!

Here is my output of lsmod | grep snd:

```

snd_mpu401              6344  0
snd_mpu401_uart         6784  1 snd_mpu401
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  2 snd_emu10k1_synth
snd_rawmidi            22816  4 snd_mpu401_uart,snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  17 snd_mpu401,snd_mpu401_uart,snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  2 snd,saa7134

```

Thanks in advance!

J

---

### Post by Duke_Of_Earl on 2006-05-09
Whoops.

Meant to add that I have run alsamixer and ensured that nothing is muted either.

---

