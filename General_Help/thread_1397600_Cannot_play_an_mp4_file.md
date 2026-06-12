---
title: "Cannot play an mp4 file"
date: 2010-02-03
forum: General Help
---

### Post by jaezcurra on 2010-02-03
Hi, I found a downloadable mp4 file at the bottom of [http://dev.chromium.org/chromium-os/user-experience/form-factors/tablet](http://dev.chromium.org/chromium-os/user-experience/form-factors/tablet)
VLC crashes while Totem plays it miserably (no sound and hardly seeable)
Any suggestion?

---

### Post by n0dix on 2010-02-03
What about any error, warning or something.  Rerun the video in console and post the output. See the logs too.

---

### Post by veggen on 2010-02-03
I'm here just to confirm the issue...

---

### Post by rocket16 on 2010-02-03
Try mPlayer, from Add/Remove install it. Then, you may use SmPlayer-System, for an excellent Front-end.

---

### Post by rocket16 on 2010-02-03
Also, checkout [http://ubuntuforums.org/showthread.php?t=414284](http://ubuntuforums.org/showthread.php?t=414284)

---

### Post by jaezcurra on 2010-02-03
Here is the result of running VLC in terminal:

> Missing reference picture
Missing reference picture
AVC: Consumed only 320 bytes instead of 326
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 279 bytes instead of 285
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 268 bytes instead of 274
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 163 bytes instead of 169
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 167 bytes instead of 173
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 2501 bytes instead of 2507
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1695 bytes instead of 1701
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
illegal short term buffer state detected
AVC: Consumed only 218 bytes instead of 224
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 235 bytes instead of 241
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 268 bytes instead of 274
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 246 bytes instead of 252
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 819 bytes instead of 825
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 792 bytes instead of 798
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 3499 bytes instead of 3505
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 2434 bytes instead of 2440
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
illegal short term buffer state detected
AVC: Consumed only 1583 bytes instead of 1589
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1549 bytes instead of 1555
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1449 bytes instead of 1455
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1400 bytes instead of 1406
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1652 bytes instead of 1658
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1693 bytes instead of 1699
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 7808 bytes instead of 7814
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 7669 bytes instead of 7675
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
illegal short term buffer state detected
AVC: Consumed only 2256 bytes instead of 2262
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 2352 bytes instead of 2358
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 9008 bytes instead of 9014
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 6913 bytes instead of 6919
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
illegal short term buffer state detected
AVC: Consumed only 2855 bytes instead of 2861
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 2898 bytes instead of 2904
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1413 bytes instead of 1419
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 1167 bytes instead of 1173
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
illegal short term buffer state detected
AVC: Consumed only 254 bytes instead of 260
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 205 bytes instead of 211
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 254 bytes instead of 260
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 205 bytes instead of 211
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 254 bytes instead of 260
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 205 bytes instead of 211
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 567 bytes instead of 573
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 477 bytes instead of 483
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
illegal short term buffer state detected
AVC: Consumed only 154 bytes instead of 160
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 138 bytes instead of 144
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 154 bytes instead of 160
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 138 bytes instead of 144
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 154 bytes instead of 160
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 138 bytes instead of 144
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 386 bytes instead of 392
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 368 bytes instead of 374
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
illegal short term buffer state detected
AVC: Consumed only 149 bytes instead of 155
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 132 bytes instead of 138
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 149 bytes instead of 155
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 132 bytes instead of 138
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 149 bytes instead of 155
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 132 bytes instead of 188
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
Missing reference picture
AVC: Consumed only 16706 bytes instead of 16712
AVC: Consumed only 6809 bytes instead of 6815
Missing reference picture
Fallo de segmentación
joseangel@ubuntu:~/Escritorio$ 


---

### Post by jaezcurra on 2010-02-03
Thanks a lot!  MPlayer worked!  There is no sound, but maybe it is a soundless clip

---

### Post by n0dix on 2010-02-03
Doble check if you have installed all the codecs.

---

### Post by jaezcurra on 2010-02-03
Everything is installed, even the SMPlayer graphical frontend.  Now I have learned that besides Totem and VLC, there is MPlayer!

---

### Post by Vaphell on 2010-02-03
lol :D

if you run mplayer from command line you get nice info about media file, video/audio codec, bitrates, framerates etc. That way you can check if there is no sound or maybe you lack some audio codec.

---

