---
title: "Avi to MP3"
date: 2006-05-28
forum: General Help
---

### Post by chakkid on 2006-05-28
Hei, guys!:) Remember me, of that thread of [no sound]("http://www.ubuntuforums.org/showthread.php?p=1052735#post1052735")?

Now i have a question.

I haved dowloaded a video that the extension is *.avi, and it's a music of comedy, with 4 minutes and all. And i want to convert it to mp3. Is this possible?:-k

---

### Post by NeghVar on 2006-05-29
I'm not sure but I'll throw it out here. Have you tried a video editer, import the video then see if you can issolate the sound part of it and create that as a seperate file? I don't think it would work but just an idea.

---

### Post by akudewan on 2006-05-29
If you want to separate the sound from a video file, you will need a video editor such as "avidemux". See homepage: [http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

I think the process is called "demultiplexing" or something

---

### Post by lha on 2006-05-29
With ```
mplayer -vo null -ao pcm:file=mywav.wav myavi.avi
``` mplayer writes myavi.avi's audio into a wav file mywav.wav. Use your mp3 encoder to encode mywav.wav into mp3.

---

### Post by canci on 2006-05-29
'n what about DVD (vob) to WAV?
Could one do that w/mplayer as well?

---

### Post by lha on 2006-05-29
[QUOTE=canci]'n what about DVD (vob) to WAV?
Could one do that w/mplayer as well?[/QUOTE]
Yes.

---

### Post by chakkid on 2006-05-29
[QUOTE=lha]With ```
mplayer -vo null -ao pcm:file=mywav.wav myavi.avi
``` mplayer writes myavi.avi's audio into a wav file mywav.wav. Use your mp3 encoder to encode mywav.wav into mp3.[/QUOTE]


I got it!:) :D Just 1 question, how do i put it to mp3? This is to wav.:confused:

---

### Post by akudewan on 2006-05-29
You can use lame. *sudo apt-get install lame* if you don't already have it
```

lame sample.wav sample.mp3

```

For more details see *man lame*

---

