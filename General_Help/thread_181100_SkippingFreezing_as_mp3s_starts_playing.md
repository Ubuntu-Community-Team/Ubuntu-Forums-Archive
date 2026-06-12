---
title: "Skipping/Freezing as mp3s starts playing"
date: 2006-05-23
forum: General Help
---

### Post by conro on 2006-05-23
I am having a problem with mp3 playback on my laptop. When i open an mp3 in xmms (or anyother program) my system pretty much freezes up for a minute or so while a second or two of the mp3 skips over the speakers. Eventually everything catches up and i can go back to doing whatever i want while the file plays in the background. 

 ls pci shows 
```

0000:00:00.1 Multimedia audio controller: Intel Corp. 82440MX AC'97 Audio Controller

``` as my audio controller
```

conor@skank:~$ lsmod | grep snd
snd_intel8x0           33248  1 
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  1 
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  2 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
conor@skank:~$ 

```
anyone know how i could go about fixing this? 
thanks!

---

### Post by FLeiXiuS on 2006-05-23
Are you steamig the music from a file server or retreiving the sound any way over the network?

---

### Post by conro on 2006-05-23
this happens both when i am playing local files, as well as if i listen to a shoucast stream. also it happens on embedded sound files such as those littering myspace.com

---

