---
title: "Viewing cell phone video on computer"
date: 2009-09-11
forum: General Help
---

### Post by DougieFresh4U on 2009-09-11
I was sent a video file from a Verizon cell phone. It was emailed to me and I can not get it to play on any thing in my system. Is it possible? I think the format is '.3g2', at least that is what is after the file. I do not have Verizon as my provider.

---

### Post by PGScooter on 2009-09-17
Hi Dougie,

I received a .3g2 as well. I could watch the video in vlc but the audio did not work. However, I extracted the audio with the following command:

```
ffmpeg -i yo4ll.3g2 -vn -ac 2 -ab 320000 audio1.ogg
```

I then just played them at the same time.

Hope it's not too late

---

