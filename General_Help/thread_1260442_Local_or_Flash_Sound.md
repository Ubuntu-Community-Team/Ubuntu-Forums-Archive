---
title: "Local or Flash Sound"
date: 2009-09-07
forum: General Help
---

### Post by kopolee11 on 2009-09-07
I have sound. However, if I listen to a flash file online (Youtube, Hulu, etc) then I can't listen to anything local. (Music, Videos, etc) And the same is true in reverse. This is the case until I restart the computer, but even then I'm still limited to listening to one thing. (Either flash or local)

I posted this question on the IRC channels and someone named "nn51200" said "you need to change some configfile that has to do with mozilla .. and add /dev/dsp to it ... Man I wish i could rember the file"

Is anyone familiar with this? If you are I would appreciate any help you could give me to fix this aggravating problem. Thanks very much!

Note: I am reposting this question in this forum, with the intent of hopefully getting more people to read it. The original post is here. [http://ubuntuforums.org/showthread.php?t=1259721](http://ubuntuforums.org/showthread.php?t=1259721)

---

### Post by CatKiller on 2009-09-07
As I understand it (and I haven't experienced this problem myself) the problem is that Flash uses OSS for sound output, and they've hard-coded the output device to be /dev/dsp. This only works if Flash can get exclusive access to the sound device. Anything else that wants to output sound is then blocked from doing so.

The other two prominent sound systems for Linux are ALSA and Pulse Audio; either of those are capable of sharing the sound device nicely. There are wrappers that you can use with OSS applications to route sound through either of those without the OSS application having any idea; it still thinks that it has exclusive access to the sound device.

*padsp* is one such wrapper, which will take OSS output and route it straight through Pulse Audio. So you could launch Firefox with ```
padsp firefox
``` Similarly, *aoss* is a wrapper that will take OSS output and route it through ALSA; you'd use that by running Firefox with ```
aoss firefox
```

I've not tried either, but they should do what you want.

---

### Post by kopolee11 on 2009-09-10
This worked! Sorta. Unfortunately, if I'm actually playing a flash video, I can't hear any local sounds. I still have to close the tab that the flash video is playing in. Still, this is better then having to restart the computer every time I want to listen to some music. 

Thank you very much!

---

