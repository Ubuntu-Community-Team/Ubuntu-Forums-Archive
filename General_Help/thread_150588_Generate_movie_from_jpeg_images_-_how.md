---
title: "Generate movie from jpeg images - how?"
date: 2006-03-26
forum: General Help
---

### Post by Muffe on 2006-03-26
I have an webcam (Creative Quickcam Pro 4000) and use a linux box to upload the images to the net every minute.

What I want is to store all the images from the last day (~1440 images) and make a movie of the images every hour. I have already made a script that saves all the images in one folder and remove all images older than 24 hours.

How do I convert this images to a movie? I guess it exist a few guides on the topic, but I can't find any... Thanks.

---

### Post by lupine_nickt on 2006-03-26
mencoder comes to mind. There's a guide here...
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html)

Should be easy enough to run as a cronjob?

xF,

...Nick

---

### Post by Muffe on 2006-03-26
Thanks for the link. I have installed both mplayer and mencoder from serveral sources (apt-get, deb from cvs, cvs etc) but I only get this error messgae:

> $ mencoder mf://*.jpeg -mf w=640:h=480:fps=25:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o output.avi
MEncoder dev-CVS-051208-17:26-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Celeron 2/Pentium III Tualatin (Family: 6, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Illegal instruction


Does anyone know what that mean? Thanks.

---

