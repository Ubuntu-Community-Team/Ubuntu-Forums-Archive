---
title: "imagemagick / graphicsmagick trim amount"
date: 2012-07-24
forum: General Help
---

### Post by &amp;)ky#)^ on 2012-07-24
I'm using graphicsmagick to trim some PNG images with transparent backgrounds.  I need to know what the offset of the new image is compared with the old one so I can reconstruct it later.

For example, take this image:
```
========
========
========
==*==*==
========
=*====*=
==*==*==
===**===
========
========
```
Then, graphicsmagick trims it to this:
```
=*==*=
======
*====*
=*==*=
==**==
```
How can I get graphicsmagick to tell me that there's now an offset of 3 pixels for y and 1 pixel for x?

---

