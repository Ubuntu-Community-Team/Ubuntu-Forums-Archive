---
title: "Errors were encountered while processing:  libglu1-mesa"
date: 2009-09-23
forum: General Help
---

### Post by lingenfr on 2009-09-23
Whenever I exexcute an apt-get, it ends with the following error.

Setting up libglu1-mesa (7.4-0ubuntu3.2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libglu1-mesa (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libglu1-mesa

I've tried a force-install. I looked at removing it, but with the dependencies, I believe it will break something. This is my Mythbuntu backend but I don't believe this is anything mythbuntu specific. I've done some searching and can't find any current bug reports with that package.

---

### Post by Domas on 2009-10-02
Same problem here. Ubuntu 9.04. Can't install libglu1-mesa from update manager.

---

### Post by lingenfr on 2009-11-08
By the time I got some feedback on my bug report, I had upgraded to KK and no longer had the issue. I got a *very helpful* reply last week saying it was a problem. Gosh.

---

