---
title: "please teach me exact command to remove a part of audio"
date: 2012-01-27
forum: General Help
---

### Post by meTroubled on 2012-01-27
I use ffmpeg to convert my mp4 videos to mp3 using this command....


>       ffmpeg -i 'input file.mp4' -acodec libmp3lame -ab 64k -ar 44100 -ac 2 'output file.mp3' 
there are some videos that have some starting dialogues and i need to remove audio for those particular seconds using ffmpeg.
How to do that ?
i want to keep same audio settings after cropping it.

Please show me what command do i use to do it...i can't figure it out using man page of ffmpeg

---

### Post by decrepit on 2012-01-27
Sorry I can't tell you about ffmpeg.
I'd be using audacity from the gui, is that possible for you?

---

### Post by meTroubled on 2012-01-27
so, i figured it out finally....

correct command is ...

```
ffmpeg -ss 30 -acodec copy -i inputfile.mp3 outputfile.mp3
```


it copies the same setting as of original file and crops first 30 seconds of it.

---

