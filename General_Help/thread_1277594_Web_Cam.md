---
title: "Web Cam"
date: 2009-09-28
forum: General Help
---

### Post by lrcaballero on 2009-09-28
Hi everyone, can someone show me how to enable my integrated Web Cam!!!

Thanks for your time and help.....:lolflag:

Luis

---

### Post by hwttdz on 2009-09-28
So I don't even know where to start, but you're going to need to at least provide some information about what sort of hardware you have, what the webcam is and what version of ubuntu you're using.  

A good start is posting the output of "uname -a" and telling us what make and model the webcam is.  Additionally if the user manual has any install directions and if you're getting any errors.  If "dmesg" has any output related to a webcam?

---

### Post by P4man on 2009-09-28
its an integrated webcam, so he may not be able to tell what type. To find out, type these commands in a terminal:

```
lspci

lsusb
```

copy/paste the output. With some luck either of these commands will list the exact webcam model.

---

### Post by lrcaballero on 2009-09-28
Thank you very much!!!!!!

I did sudo modprobe uvcvideo
       sudo apt-get install cheese
       cheese
and presto!!!!!!!!

---

