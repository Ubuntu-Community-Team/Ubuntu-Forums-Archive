---
title: "How to get troublesome webcams to work with FlashPlayer 10+"
date: 2010-02-04
forum: General Help
---

### Post by scotty64 on 2010-02-04
Me and a lot of other people have problems with using certain webcams (e.g. the Philips SPC900NC) with FlashPlayer version 10 and higher (the latest 10.1 betas).
Here is a workaround that gets these cameras going by preloading the V4L1 compatibility library. Use the following command line if you use firefox:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

enjoy !

---

### Post by DPic on 2010-03-17
Thank you so much! That worked xD

For other people who want more information: [http://ubuntuforums.org/showthread.php?p=8978659#post8978659](http://ubuntuforums.org/showthread.php?p=8978659#post8978659)

Also, you should vote for Adobe to fix this bug! 
[https://bugs.adobe.com/jira/browse/FP-204](https://bugs.adobe.com/jira/browse/FP-204)

---

### Post by JoZ3 on 2010-03-18
not work for my webcam in firefox with lastest flash plugin

i have a ubuntu 9.10 64 bits and my webcam a creative labs (vf-0050)

The webcam work fine in Opera with same plugin version and without preloading the V4l1 compatibility library

---

### Post by scotty64 on 2010-03-29
> **JoZ3 said:**
> not work for my webcam in firefox with lastest flash plugin

i have a ubuntu 9.10 64 bits and my webcam a creative labs (vf-0050)

The webcam work fine in Opera with same plugin version and without preloading the V4l1 compatibility library

I am not an expert in the 64bit Ubuntu flavour, but I am assuming that 64bit Ubuntu stores the 32bit libraries in a different path - and you probably need a 32bit V4L1 compatibility library as FlashPlayer - at least as far as I know - is still 32bits.

---

### Post by gyurman on 2010-04-02
The all of browser are a sit inside ubuntu 9.10
Firefox cannot show flash application, only video.
Opera enough if I click on settings panel, immediately crash.
Chromium same doing. But I can load of fist web page for half. Under crash.
Maybe are my anything wrong?
KDE 4.4.2
Linux 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux
flash 10.0.45.2
firefox 3.6.4
opera 10.10.4742
chromium 5.0.368

How do you think? Anybody have probe for another linux? I know opensolaris doesn't support much more hardware.

---

