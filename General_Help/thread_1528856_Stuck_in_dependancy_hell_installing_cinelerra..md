---
title: "Stuck in dependancy hell: installing cinelerra."
date: 2010-07-11
forum: General Help
---

### Post by Tamalin on 2010-07-11
Ok, an attempt to have cinelerra installed on my Ubuntu 10.04 desktop has left me trawling the internet for missing dependencies.  I don't know what to do anymore, after dealing with a problem with liblame0 not being compatible with libmp3lame0 or something, which is required by libmjpegtools0.
When installing cinelerra I do receive the following error:

> cinelerra:
 Depends: liblame0 (>= 3.97)
 Depends: libmjpegtools0 (>=1:1.8.0) but it is not installable
 Depends: libopenexr2ldbl (>=1.2.2) but it is not installable
 Depends: libquicktimehv but it is not going to be installed
 Depends: libraw1394-8  but it is not installable
 Depends: libquicktimehv but it is not going to be installed

I'm pretty sick of this now.  Does any one have any advice or help?
Thank you in advance.

---

### Post by User-007 on 2010-07-11
Hi,

Have you followed these instructions: [http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php) ?

It seems that updating your sources.list with one more repository should be enough?

User JB

---

