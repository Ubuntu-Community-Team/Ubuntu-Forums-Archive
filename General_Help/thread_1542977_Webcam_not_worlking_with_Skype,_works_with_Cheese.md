---
title: "Webcam not worlking with Skype, works with Cheese"
date: 2010-07-31
forum: General Help
---

### Post by elidoperezmd on 2010-07-31
Hi all...

I have used my webcam with skype before in several ocations, but now im not able to do so. The wencam works with cheese, so i dont now where to got form here.

On skype video options, it shows only one video/webcam device (CNF7017 (/dev/video0). when i with test on the options shows a gray screen, which is the same that im sending to my contacts when we video chat...

what should i do?

thanks for your time/replies/help

---

### Post by elidoperezmd on 2010-07-31
bump

---

### Post by no2498 on 2010-07-31
see if this helps
open a terminal put this in it

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


hope that helps

---

### Post by elidoperezmd on 2010-07-31
> **no2498 said:**
> see if this helps
open a terminal put this in it

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


hope that helps

HI, thanks for the help, i took your advice and went in the terminal, after entering the command the terminal show this message 

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

and then opens the skype...then i went into options and hitted the test button it shows many of tis messages, and of course the test did not show the webcam;

X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes)

i tried calling again and the thing is that my webcam is sending a good image, but i dont see the other's person webcam, and is not their problem, i have tried with many diferent contacts

what do i do now? thanks

---

### Post by elidoperezmd on 2010-08-05
bump

---

### Post by elidoperezmd on 2010-08-14
bump

---

### Post by elidoperezmd on 2010-08-18
bump

---

### Post by Cpierce on 2010-08-19
This worked for me

[http://ubuntuforums.org/showthread.php?t=1546777](http://ubuntuforums.org/showthread.php?t=1546777)

---

### Post by elidoperezmd on 2010-08-20
> **Cpierce said:**
> This worked for me

[http://ubuntuforums.org/showthread.php?t=1546777](http://ubuntuforums.org/showthread.php?t=1546777)

thanks for the help... id did not work for me though, seems that you had the very same promblem that im having

---

### Post by elidoperezmd on 2010-08-23
skype says that my video device is located in /dev/video0  is this accurate?

---

