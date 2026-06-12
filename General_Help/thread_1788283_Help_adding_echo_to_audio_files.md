---
title: "Help adding echo to audio files"
date: 2011-06-22
forum: General Help
---

### Post by StuartN on 2011-06-22
Can anyone suggest a simple, scriptable method of adding echo (and compression / limiting / any other effect) to an audio file?

I have sheet music (lessons) coded to MIDI and currently convert this to MP3 using Timidity and lame, which sounds fine for many tracks. I would like to add a little stereo ambience to make mono tracks less fatiguing on MP3-player headphones.

```
filename=$(basename $1 .mid)
timidity $filename.mid -Ow -o $filename.wav
lame $filename.wav $filename.mp3
```

---

### Post by sanderd17 on 2011-06-22
Is this better?

```
filename=$(basename $1 .mid)
timidity $filename.mid -OwS -o $filename.wav
lame $filename.wav $filename.mp3
```

note the S for stereo

---

### Post by StuartN on 2011-06-23
> **sanderd17 said:**
> Is this better?

note the S for stereo

Thanks. Despite the manual entry, the default output from Timidity seems to be a stereo file - the two files are identical in Audacity. In both cases the two channels are identical for a mono instrument panned to centre. It is also necessary to hard-code the reverb depth into the MIDI file, which is a pain when converting a music course of many pieces, and the reverb appears to be dual-mono (i.e. it generates two identical output channels).

However, the manual does offer the suggestion to pipe the output through Sox, and Sox permits the use of Freeverb which generates a stereo reverb effect with several parameters (reverberance, HF-damping, room-size and stereo-depth, all as %). This is what I have after a play, which is a distinct improvement on the dry MIDI output:
```
timidity $filename.mid -OwS -o - | sox -t wav - $filename.wav reverb 30 20 30 70
lame $filename.wav $filename.mp3
```

---

