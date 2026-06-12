---
title: "Join 2 mp4 files into 1?"
date: 2010-12-16
forum: General Help
---

### Post by PDA1 on 2010-12-16
How can I combine 2 video files into 1 using FFMPEG?  I've tried the following command......


cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg


....the result being only 1 of the video files combined but the overall file size is equivalent to the 2 files combined together.

Please don't suggest Avidemux- the version I have on my machine won't do it.

Any ideas?

---

### Post by pellgarlic on 2010-12-17
hi. i don't think ffmpeg can do it "internally" - you'd have to use ffmpeg to convert the video files to a format which _can_ be "cat"ted together.

either that, or maybe mencoder could do it:

[http://ubuntuforums.org/showthread.php?t=1400598](http://ubuntuforums.org/showthread.php?t=1400598)

---

