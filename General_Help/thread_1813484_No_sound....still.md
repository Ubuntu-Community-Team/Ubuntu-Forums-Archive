---
title: "No sound....still"
date: 2011-07-27
forum: General Help
---

### Post by SevenHundred on 2011-07-27
I'm new to Linux and I have just installed Ubuntu 11.04. I don't have any sound and have tried every solution I could find on the forums and gotten nowhere. Maybe this will help, when I type in this prompt:

aplay -l | grep card

I get this:

card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]

When I type in this:

sudo lsmod | grep snd

I get this:

snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm


I don't really know what any of that means since I'm not very familiar with command lines, but maybe that will mean something to someone.

---

