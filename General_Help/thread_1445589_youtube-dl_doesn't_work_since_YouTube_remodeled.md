---
title: "youtube-dl doesn't work since YouTube remodeled?"
date: 2010-04-02
forum: General Help
---

### Post by gfunkera on 2010-04-02
i use youtube-dl quite alot and recently YouTube changed its website and ive noticed that the program (youtube-dl) doesnt extract the video anymore (or sound; it fails completely)

anyone have a fix to this?

---

### Post by lisati on 2010-04-02
Might be too soon. It's possible that Youtube have put something in place in response to people downloading the videos.

Caution: see this thread: [http://ubuntuforums.org/showthread.php?t=1440973](http://ubuntuforums.org/showthread.php?t=1440973)

---

### Post by ron999 on 2010-04-02
> **gfunkera said:**
> i use youtube-dl quite alot and recently YouTube changed its website and ive noticed that the program (youtube-dl) doesnt extract the video anymore (or sound; it fails completely)

anyone have a fix to this?
There's a new version available today. From here:-[http://bitbucket.org/rg3/youtube-dl/src/e9b7ee97f3b0/]("http://bitbucket.org/rg3/youtube-dl/src/e9b7ee97f3b0/")
Replace the script that's in your usr/local/bin folder. Put the new one in there instead.

---

### Post by fragos on 2010-04-03
Note that when you view a video in a browser it almost always buffered in /tmp. It may have a strange name but you can move it to whatever folder you save videos in.

---

### Post by kokkus on 2010-04-03
It's actually /usr/bin but ok

---

### Post by Vaphell on 2010-04-03
youtube clips? they are definitely stored in /tmp on my box

---

