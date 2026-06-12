---
title: "recording streaming audio"
date: 2006-06-21
forum: General Help
---

### Post by jordilin on 2006-06-21
I try to record streaming audio or any audio that goes through my computer. I do the following, once I set up the audio controls:
$ arecord -f cd -t raw | lame -x - out.mp3
This little command records the audio that goes through your computer and encodes it directly to an mp3 file. It records the audio very well, except that I don't know why it only records one channel. I mean, it only sounds in one of the earphones  instead of both. 
Anyone has tried to record audio and has experienced something similar. Or, there are other methods?
thanks

---

### Post by bionnaki on 2006-06-21
streamtuner + streamripper works.

or just record with audacity.

---

### Post by vigleik on 2006-06-21
Did you try with the "-c 2" option?

Vigleik

---

### Post by jordilin on 2006-06-21
[QUOTE=vigleik]Did you try with the "-c 2" option?

Vigleik[/QUOTE]
Yes I tried the -c 2 option, and no result. In fact, the -f cd option is equivalent to:
-f cd (16 bit little endian, 44100, stereo [-f S16_LE -c2 -r44100]
I don't know if you can hear in both channels any sound recorded, right+left earphones.

---

### Post by jordilin on 2006-06-21
I have just tried audacity, and it records with both channels. The problem is that it doesn't record directly to mp3, which is a problem if you are recording radio for lots of hours. If you record using audacity, once recorded you have to export to mp3, which can be a pain.

---

### Post by Quirky on 2006-06-21
I use mplayer. URL is the url of the stream (if it is a playlist, which mmost seem to be)

```
mplayer -cache 512 -playlist $URL -ao pcm:file=output.wav -vc dummy -vo null
```

---

### Post by jordilin on 2006-06-21
[QUOTE=Quirky]I use mplayer. URL is the url of the stream (if it is a playlist, which mmost seem to be)

```
mplayer -cache 512 -playlist $URL -ao pcm:file=output.wav -vc dummy -vo null
```[/QUOTE]
Yes, but you are recording to a wav file, aren't you? The trick here, is using the powerful feature of recording straight ahead to an mp3 file, without going through an intermediate sound file, which is wav (not compressed, so it takes lots of space when recording).

---

