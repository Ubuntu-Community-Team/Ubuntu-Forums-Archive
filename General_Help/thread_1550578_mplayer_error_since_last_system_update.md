---
title: "mplayer error since last system update"
date: 2010-08-11
forum: General Help
---

### Post by davrosuk on 2010-08-11
Since my last system update yeasterday afternoon mplayer returns an error. Another system which I have yet to run the update on is still fine. Both systems are Ubuntu 10.04 Lucid Lynx.

The error is:

```
mplayer: relocation error: mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference
```

Anyone have any thoughts or suggestions?

---

### Post by luigi_mb on 2010-08-11
I guess the updates from ppa:c-korn/vlc had some serious problem, and they broke mplayer/smplayer and probably other components (both 32-bit and 64-bit). I noticed that today they are no longer offered. I assume they were withdrawn.

It's not clear to me how to undo the damage. Any suggestions?

/luigi

---

### Post by endotherm on 2010-08-11
I tend to use the mplayer/smplayer ppas as the repo versions are very old:
[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")
[https://launchpad.net/~rvm/+archive/smplayer]("https://launchpad.net/%7Ervm/+archive/smplayer")

along with the w64codecs from the medibuntu repos, and have not had trouble with the latest libavcodec update.  you might want to try updating it from there.

---

### Post by XerXeX on 2010-08-11
Same problem here, mplayer stopped working after the update. The update also un-installed dvd:copy and dvd95 and messed up a few other things. I usually react when the update wants to remove apps, this time I missed it. There is no way for me to re-install those DVD apps and mplayer is dead!

---

### Post by davrosuk on 2010-08-11
I've managed to solve it, but I don't really fully understand why...

I installed ffmpeg from the repo's and then everything started working. As part of the install it removed libformat52 and replaced it with, well, something else. The good news it doesn't appear to have have broken anything else!

---

### Post by toll on 2012-04-19
Yes, somehow but superuser`s apt-get install ffmpeg helped. :popcorn:

---

