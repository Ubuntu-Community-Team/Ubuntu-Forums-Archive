---
title: "timidity alsa emulation failure"
date: 2006-04-15
forum: General Help
---

### Post by the_padawan on 2006-04-15
Hello all,

On startup/shutdown, the step  * Starting TiMidity++ ALSA midi emulation...  consistently reports a red failed. I have installed midi capabilities with automatix. 

Trying to start it manually from the terminal gives this error:

```
 $ sudo /etc/init.d/timidity start
 * Starting TiMidity++ ALSA midi emulation...                                                                                                               ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 32
CHANNELS: 2
RATE: 44100
PERIOD_TIME: (2333 3667)
PERIOD_SIZE: (73 256)
PERIOD_BYTES: (292 30108)
PERIODS: (0 207)
BUFFER_TIME: (11609 341316)
BUFFER_SIZE: 512
BUFFER_BYTES: [2048 60208]
TICK_TIME: 1000
```


And of course, the red fail message

I can sometimes use timidity from the command line. Usually it tells me that /dev/dsp is busy.

Any ideas?

---

### Post by the_padawan on 2006-04-17
Bump
Any ideas at all?

---

### Post by @jens on 2006-04-27
I played around a lot with timidity/MIDI/Noteedit and so on (Debian Box). What I do is: 
1) loading the sequencer module -> sudo modprobe snd-seq
when you want to start the module automaticly, edit /etc/modules->snd-seq
2) starting timidity in Alsa-server-mode-> sudo timidity -iA -B8,2 -Os

hth
@jens

---

