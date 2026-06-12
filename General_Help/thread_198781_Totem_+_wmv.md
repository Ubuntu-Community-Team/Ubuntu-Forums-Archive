---
title: "Totem + wmv"
date: 2006-06-17
forum: General Help
---

### Post by DoctorMO on 2006-06-17
The totem movie player will not play the video section of wmv files, the error I get when run from the command line is:

** Message: don't know how to handle video/x-wmv, wmvversion=(int)3, framerate=(fraction)25/1, width=(int)320, height=(int)240, codec_data=(buffer)4ff91

so my gues is that it doesn't understand the mime type. even with all the multiverse, bad and ugly packages installed.

does anyone know enough about mime types to fix this or is this a problem with totem needing to be compiled with more mime types?

---

### Post by DoctorMO on 2006-06-17
Same thing for real media:

Message: don't know how to handle video/x-pn-realvideo, rmversion=(int)4, format=(int)1073750016, subformat=(int)528416, width=(int)320, height=(int)240, framerate=(fraction)30/1

DivX, mpeg, mpeg2, ogg theora check out fine though.

---

### Post by DoctorMO on 2006-08-22
solution involved installing xine instead of gstreamer following guide on ubuntu wiki.

---

