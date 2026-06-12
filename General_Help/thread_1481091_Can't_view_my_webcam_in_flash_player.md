---
title: "Can't view my webcam in flash player"
date: 2010-05-12
forum: General Help
---

### Post by salman4u on 2010-05-12
Hello,
I always get "no camera found" in camera tab in flash player settings :(. What can be the problem. My camera is working fine. I have flash player also installed and working absolutely fine.

I tried viewing my camera with "cheese" and i can perfectly see it. But i am unable to see it with Flash player. I visited ustream.tv to see if i can broadcast my video but it always shows "no camera found" in camera tab. How do i resolve this? I even tried solution posted in this thread [http://ubuntuforums.org/showthread.php?t=1148480](http://ubuntuforums.org/showthread.php?t=1148480) :-

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &

But still it doesn't work. I also tried gkstreamer-properties and my webcam works just fine in video for linux 2. 

Please, help me. I have been trying to solve this since 3 hours. Waiting for your replies :)

UPDATE :- i am now able to view my webcam :) using the command given above. But how do i the same for chrome?
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so chrome & doesn't work :(

---

### Post by no2498 on 2010-05-12
have you tried 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash

dont know if it works or not just asking

---

### Post by lleachii on 2010-06-09
Please visit [https://bugs.adobe.com/jira/browse/FP-775]("https://bugs.adobe.com/jira/browse/FP-775") to track the bug report and vote for this issue.

---

### Post by no2498 on 2010-06-09
i have flash 10.45 installed on 2 copmuters 1 is 804 cam works good
the other is 910 i can get it to see the cam with flash 
just the color's is grb not rgb
if you look at the time frame this is the time ubuntu give cheese all the webcam settings

---

