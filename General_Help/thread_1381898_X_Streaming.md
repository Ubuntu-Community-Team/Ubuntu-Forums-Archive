---
title: "X Streaming?"
date: 2010-01-15
forum: General Help
---

### Post by Amaroq on 2010-01-15
Heya. I'm really curious, is it possible to stream a window from X, as opposed to forwarding it over SSH?

I've used X-forwarding before so that I could ssh into another computer and open up a graphical program and have it show up on mine. But as far as I know, that window only opens on your computer, not on the computer the program is actually running on.

Is it possible for me to open a window on my computer, and to sort of X stream it to another computer that has X so they can watch what I'm doing in that window?

---

### Post by Lars Noodén on 2010-01-15
You can record X sessions with ffmpeg and you can stream video with ffmpeg.
I would guess that you could then stream X sessions, but I haven't tried it.  

[http://ffmpeg.org/ffserver-doc.html](http://ffmpeg.org/ffserver-doc.html)
[http://www.elpauer.org/?p=261](http://www.elpauer.org/?p=261)
[http://internetarchive.wordpress.com/2008/11/25/fast-and-reliable-way-to-encode-theora-ogg-videos-using-ffmpeg-libtheora-and-liboggz/](http://internetarchive.wordpress.com/2008/11/25/fast-and-reliable-way-to-encode-theora-ogg-videos-using-ffmpeg-libtheora-and-liboggz/)

If it does work, post how.  It'd be really cool to be able to multi-cast a stream out to many users for presentations, demos or lectures.

---

