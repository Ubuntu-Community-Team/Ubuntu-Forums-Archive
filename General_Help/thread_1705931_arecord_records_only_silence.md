---
title: "arecord records only silence"
date: 2011-03-13
forum: General Help
---

### Post by gemorgan on 2011-03-13
Hi All,

I can't get arecord to record any sound. I've tried running firefox with some streaming stuff or even just playing a song with totem from a mp3 on my hard drive. I'm running ```
arecord -D default -d10440 -r16000 -c1 test.wav
```but the resulting test.wav has no sound in it.

I'm running maverick as installed. What gives?

Thanks!

---

### Post by pjbgravely on 2011-04-14
I just solved mine, it was frustrating. Try going to alsamixer in the command line, click F4, the randomly raise levels with page up until it works. You toggle capture on inputs with the space bar. I had to raise and toggle everything before it would finally record. I hope your inputs are correctly labelled in alsamixer.

Paul

---

### Post by Jose Catre-Vandis on 2011-04-14
That's the place to look (alsamixer then f4) but this might reveal that your sound card cannot capture the sound "playing on the computer". Mine can't (well, unless I fiddle around with jack and pulseaudio, neither of which I have installed!). Also try:
```
aplay -l
aplay -L
```to see what your card can do

---

### Post by NFblaze on 2011-04-14
I used to have a similar problem with sound though I never tried to record. Though my internal sound system (which Im assuming arecord uses to record) would not work even though my external speakers worked. So basically, I would be assed out when plugging in an earphone unless I went to alsamixer in the commandline and increasing the PCM channel up.

Try it out.

---

