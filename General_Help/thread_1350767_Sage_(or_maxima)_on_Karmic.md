---
title: "Sage (or maxima) on Karmic"
date: 2009-12-09
forum: General Help
---

### Post by starwed on 2009-12-09
I installed sage (mathematical software) on 9.10, and it seems fairly broken.  (This refers to the version in the official repo.)  Frequently when trying some basic examples from the tutorial it will crash, always with Maxima as the culprit.

Does anyone know of any fixes for this?

---

### Post by mionescu on 2009-12-09
You are right that maxima crashes a lot in 9.10. It is basically unusable. There are other threads which contain links to a bug report where you can find a workaround. I chose to download the latest version of sage from their website 
[http://www.sagemath.org/download-linux.html](http://www.sagemath.org/download-linux.html)
It has many additional features compared with the version in the official version and it works great.

---

### Post by starwed on 2009-12-10
> There are other threads which contain links to a bug report where you can find a workaround.

For the record, I can't find any such threads on this forum.  I previously found a [bug report](https://bugs.launchpad.net/ubuntu/+source/sagemath/+bug/487088) on the issue in launchpad, but it didn't contain a workaround.

---

### Post by mionescu on 2009-12-10
The bug report is
[https://bugs.launchpad.net/ubuntu/+source/maxima/+bug/303587](https://bugs.launchpad.net/ubuntu/+source/maxima/+bug/303587)

Some people said that comment #14 worked for them. I did not try it, because I use the latest sage version downloaded as I mentioned above.

---

### Post by Ultros88 on 2010-01-09
Sorry for hijacking this thread. I didn't feel my issue warrants a new one, and I wanted to ensure that people interested in Sage read this post.

When I run the graph example from the graphics quickstart guide the output doesn't fully include the vertices. Is there some way around this?

Thanks and... let me know if this should have warranted a new thread

---

### Post by process91 on 2010-01-15
I have created a small [howto as well as an automated script]("http://ubuntuforums.org/showthread.php?t=1382405&highlight=sagemath+karmic") which downloads, compiles, and installs sage 4.3 on Karmic Koala. I found there were errors with both the version in the repository, as well as the binary. I have had good results from the version compiled as I describe in the how to.

---

