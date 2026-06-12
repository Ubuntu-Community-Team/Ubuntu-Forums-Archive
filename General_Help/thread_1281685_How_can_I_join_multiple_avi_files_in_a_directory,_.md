---
title: "How can I join multiple avi files in a directory, bash script help?"
date: 2009-10-03
forum: General Help
---

### Post by little_penguin on 2009-10-03
Does anyone know how I can join all the video files in a directory automatically into a single file, using say the asterisk wildcard or similar? Or is there a better way? A bash script?

I have over 100 short .avi files in a directory which I would like to join into one big file. I can do "cat file1 file2 file3 > outputfile" etc, but not for 100 files. I googled it and looked in the forums but most people only seem to be joining 2 or 3 files together...

Any ideas? 

Thanks in advance!
LP

---

### Post by credobyte on 2009-10-03
```
mencoder -oac copy -ovc copy -idx -o megavideo.avi *.avi

```

---

### Post by little_penguin on 2009-10-03
Wow, that was quick - it worked, thanks!

---

### Post by rob1408 on 2009-10-03
Avidemux is a great little tool.  Sort of like Virtualdub mod, nice GUI and its simple to use.

---

### Post by little_penguin on 2009-10-03
Thanks, yes I use Avidemux quite a bit for converting, it's great. But I didn't realize you can just drag all the avis and drop them into the avidemux window, hit Save and join the files into one file that way. Or alternatively use the Append function.

---

### Post by fugazi32 on 2009-10-03
> **credobyte said:**
> ```
mencoder -oac copy -ovc copy -idx -o megavideo.avi *.avi

```

Will this work for converting multiple **.flv* files into a single **.avi* or **.mpg* --??

---

### Post by credobyte on 2009-10-03
> **fugazi32 said:**
> Will this work for converting multiple **.flv* files into a single **.avi* or **.mpg* --??

Haven't tried ( that's why we have ffmpeg ), tough, I don't see a single reason why it shouldn't work.

---

