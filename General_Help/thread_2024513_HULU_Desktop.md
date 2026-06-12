---
title: "HULU Desktop"
date: 2012-07-13
forum: General Help
---

### Post by rchar66 on 2012-07-13
I'm not sure where to put this thread, so I'm just going to put it here.

I had the HULU Desktop for Linux running in 11.10. When I upgraded to 12.04 it broke Hulu Desktop.

I tried downloading HULU desktop again and re-installed it, but it still won't run.

Has anybody else had a similar issue with HULU Desktop on 12.04?

Richard

---

### Post by gschoper on 2012-07-13
I ran into the same issue after a recent flash update. I downloaded flashplayer11_1r102_63_linux.i386.tar.gz (unfortunately I don't remember where from) and placed libflashplayer.so in ~/lib

I then edited ~/.huludesktop and changed the following line to point to the older version of flash:

```
[flash]
flash_location = /home/g/lib/libflashplayer.so

```

This will only affect flash for hulu and not other apps dependent upon flash.

UPDATE: Can be downloaded from [https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads)

HTH,

G

---

