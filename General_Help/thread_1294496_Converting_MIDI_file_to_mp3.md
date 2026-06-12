---
title: "Converting MIDI file to mp3"
date: 2009-10-18
forum: General Help
---

### Post by John Jones on 2009-10-18
Can anybody point me towards an application that will allow me to convert midi files into mp3/wav files, please?

I've looked through the repositories and googled this query, but I can't find anything.

Thanks,

John Jones

---

### Post by Sam on 2009-10-18
Install [timidity](apt:timidity)
```
timidity -Ow *file.mid*
```
This will create a *file.wav* in the working directory.

---

### Post by Chronon on 2009-10-18
TiMidity++ will convert the MIDI instructions into PCM audio.  You can take this WAV and convert it to any format you like.

---

### Post by John Jones on 2009-10-18
Excellent. Thanks to you both.

John

---

