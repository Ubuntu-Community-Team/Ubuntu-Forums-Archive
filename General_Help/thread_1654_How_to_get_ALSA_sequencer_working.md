---
title: "How to get ALSA sequencer working?"
date: 2004-10-22
forum: General Help
---

### Post by Flawed on 2004-10-22
I have a SB Live and would like to be able to use Rosegarden 4. Unfortunately, I can't seem to get the RG sequencer to start properly. Even though JACK is started, I keep on getting this error:

ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

In the KDE Sound Info Center it says: Synth Devices: NOT ENABLED IN CONFIG. 
How do I enable those? I don't have any problems with sound output, though. Lots of thanks in advance.

I only got the Live card yesterday, by the way, it replaced my crappy onboard sound card, which I disabled. Does this mean I may have to reinstall Ubuntu?

---

### Post by Flawed on 2004-10-23
Let's try a slight bump.

---

### Post by banadushi on 2004-12-19
modprobe snd-seq-oss

---

### Post by macewan on 2004-12-24
[QUOTE=banadushi]modprobe snd-seq-oss[/QUOTE]
 [http://alsa.opensrc.org/](http://alsa.opensrc.org/)

read through these

---

### Post by piedamaro on 2004-12-24
[QUOTE=banadushi]modprobe snd-seq-oss[/QUOTE]
Yes but without
modprobe snd-emu10k1-synth
you'll go nowhere.

---

### Post by alainhenry on 2004-12-27
I managed to have timidity working as midi server with alsa.  It might help you.  See thread: 
[http://www.ubuntuforums.org/showthread.php?t=8286](http://www.ubuntuforums.org/showthread.php?t=8286)
or wikipage [http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo](http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo)
Alain

---

### Post by Flawed on 2005-06-28
This is odd, I followed the howto and it worked once. When I tried it for the second time, I got the following error:

```
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 2048, period size 1024 bytes
TiMidity starting in ALSA server mode
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
error in snd_seq_open
```

---

### Post by alainhenry on 2005-06-28
I have no idea what it could be.  Are the modules still loaded when the error occurs?  
Alain

---

### Post by Flawed on 2005-06-29
Strangely, enough, the problem went away. I've now come [this](http://www.ubuntuforums.org/showthread.php?t=45058) far. :D

---

### Post by creezz on 2005-08-06
[QUOTE=Flawed]This is odd, I followed the howto and it worked once. When I tried it for the second time, I got the following error:

```
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 2048, period size 1024 bytes
TiMidity starting in ALSA server mode
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
error in snd_seq_open
```[/QUOTE]

I also tried setting up timidity and it only worked once. When I try to to play midi file again using pmidi, I always got the following errors and there is no sound appear:

```

Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 60208, period size 7524 bytes
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 60208, period size 7524 bytes
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 60208, period size 7524 bytes
```

I've also try to play midi using fluidsynth, but while I started fluidsynth, I can't play mp3 using other player. I need to close fluidsynth first (not only to stop the midi played). Is there a way that I could play them together???????

Any ideas, please?

---

### Post by slowwalk on 2005-08-07
A way to make the "modprobe snd_seq_oss"
"durable" is to add "snd_seq_oss" to the file /etc/modules

I did it and my problems where gone.

BTW, this issue is already reported to the ubuntu developpers?
A newbie should have to deal with this kind of issues...

cheers,
MarC

---

