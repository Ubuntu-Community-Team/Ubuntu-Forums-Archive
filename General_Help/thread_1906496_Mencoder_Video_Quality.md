---
title: "Mencoder Video Quality"
date: 2012-01-09
forum: General Help
---

### Post by bootstrap58 on 2012-01-09
Hello. Im adding subtitle to myvideo. There are no problem. But my video quality decreases. (I must convert to FLV)

I want to keep my source video quality (good or bad not important)

My destination video quality must be same with source video

My mencoder command is below

```
mencoder -utf8 -vf pp=de -ovc lavc -lavcopts vcodec flv:vbitrate:150 -sub c:\deneme.srt -o c:\output.flv c:\mysource.avi
```

Inadvance thanks

---

