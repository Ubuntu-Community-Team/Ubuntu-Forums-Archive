---
title: "Webcam stopped to Work!"
date: 2011-07-07
forum: General Help
---

### Post by felipeabrao on 2011-07-07
Hello, everybody!

I use Ubuntu 11.04 in my laptop Dell Vostro 1510, and had not had any problem with my webcam until this week. It used to work perfectly, even in Skype, but suddenly it stopped to work. I really do not know what could have happened. If you have any ideas, I would appreciate it. Thanks in advance,

Felipe

---

### Post by no2498 on 2011-07-07
if you can get this to open/run it may help you

in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

play with this till cheese sees the cam

---

### Post by felipeabrao on 2011-07-07
Thank you for your help, no2498. I did what you suggested, but I could find out that I do not have the two options that you mentioned: v4l and v4l2. I have just v4l2, and when I clicked the buttom to test it, there was an error message. Maybe I can install v4l, but I do not know how to do it! I am sorry, I do not understand much about Linux...

Thanks again!

---

### Post by no2498 on 2011-07-08
ok try this in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype   click enter


they have been changing gstreame on us

if that works for skype save it to your desk top

then try it for cheese

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

save them  you will need to do it every time you use skype or cheese

later you can make them a bin/bash file

---

### Post by no2498 on 2011-07-09
this should help you

[http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html](http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html)

---

### Post by felipeabrao on 2011-07-09
Thank you again, no2498. Unfortunatelly it did not work again. But thanks anyway.

---

### Post by no2498 on 2011-07-09
look in your package manager for gstreamer
you need a good set , bad set , ugly set , and a 0.10 for the ubuntu you use

---

### Post by felipeabrao on 2011-07-09
Thank you once more, no2498! I did some things that you told me, but they did not work at the moment. However, I do not know if it was a coincidence or not, when I turned my computer off and then later on again, the webcamera simply came back to life! I can not explain what happened! Well, thank you very much for your help!

Felipe

---

### Post by no2498 on 2011-07-10
you are welcome

mark this as solved

---

