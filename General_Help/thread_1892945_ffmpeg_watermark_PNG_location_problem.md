---
title: "ffmpeg watermark PNG location problem"
date: 2011-12-09
forum: General Help
---

### Post by bootstrap58 on 2011-12-09
Hello. sorry for my bad english.

I'm adding watermark on my video without problems. I have 2 scenarios.

**Scenario 1 (Working)**

in this scenario mylogo.png in same direcroty with ffmepg.exe

```
ffmpeg -i c:\myvid.flv -vf "movie=mylogo.png [logo]; [in][logo] overlay=0:0 [out]" c:\mynewvid.flv
```

**Scenario 2 (Not Working)** :(

in this scenario mylogo.png is in another directory

```
ffmpeg -i c:\myvid.flv -vf "movie=d:\mypictures\mylogo.png [logo]; [in][logo] overlay=0:0 [out]" c:\mynewvid.flv
```ffmpeg changes mylogo path to **:\mypictures\mylogo.png**  and giving errror message.

so losing **D** drive LETTER . how can i solve this problem.

thanks for your relations.

---

### Post by bootstrap58 on 2011-12-09
Bump

---

### Post by FakeOutdoorsman on 2011-12-10
I don't mind answering FFmpeg questions from Windows users here, but your issue seems fairly Windows specific (what's a drive letter?). Please ask your question at the [ffmpeg-user](https://lists.ffmpeg.org/mailman/listinfo/ffmpeg-user/) mailing list or the #ffmpeg IRC channel. We try to answer most questions at ffmpeg-user, but be patient. We are all volunteers and can't answer every question or don't always have an answer.

---

