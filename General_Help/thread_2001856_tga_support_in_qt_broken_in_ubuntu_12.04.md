---
title: "tga support in qt broken in ubuntu 12.04?"
date: 2012-06-11
forum: General Help
---

### Post by schleppel on 2012-06-11
Loading a tga image in c++/qt fails every time.

```

test = QImage("test.tga", "")

```
returns an empty image - width 0, height 0.

Two weeks ago the same code worked for me, so I guess one of the last qt updates broke something.

It isn't just my code having problems with tga's.
For example
"gwenview test.tga" fails to load the image as well.

I'm running an up-to-date ubuntu 12.04 x86_64.

---

