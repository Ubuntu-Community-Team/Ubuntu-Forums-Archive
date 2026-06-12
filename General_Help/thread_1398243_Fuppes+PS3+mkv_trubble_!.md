---
title: "Fuppes+PS3+mkv trubble !"
date: 2010-02-04
forum: General Help
---

### Post by Cerox Rex on 2010-02-04
Heya.

I'v just installed Fuppes on my 9.10 server box and it seems to work great.

However I have a few .mkv files that dosnt show up.

Is there a way to make .mkv work on my PS3 with fuppes?
My guess is I have to transcode som how as the PS3 still have lousy format support.

Also how do i make fuppes start at boot as a service?

---

### Post by Shhnap on 2010-02-04
I looked at what you said in your other post and to me it looks like you have not typed in --enable-transcoder-ffmpeg as an option to ./configure. Like so:

```
./configure --enable-transcoder-ffmpeg --your-other-options-here
```

So you should try that first and see what results you get. However, I have had a few problems with transcoding recently so let me know what the results are.

I hope this helps.

---

### Post by Cerox Rex on 2010-02-05
Thnx for the help. I now seem to have transcoding enabled, but my PS3 dosnt recognise any of my .mkv files. Tried recompiling several times now, result is still the same.

The transcoding part of my .cfg file seems ok so i dont belive thats the problem.

---

