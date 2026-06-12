---
title: "Problem while installing OpenCV to ubuntu 11.10"
date: 2012-03-03
forum: General Help
---

### Post by shasar on 2012-03-03
I have been trying to resolve the errors that prevented me from  compiling the e-Lamp application,but I have come across certain  bottlenecks during the process,
In a nutshell,

1.The installation of Open CV 2.3.1 is failing due to the following errors,
 
make[2]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_ffmpeg.o] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2

The appropriate step was followed to solve them as given in this link:
  
[https://code.ros.org/trac/opencv/ticket/1020](https://code.ros.org/trac/opencv/ticket/1020) ,which was to add the patch but still the 2 errors prevailed.

Can anyone help...thanks in advance!

---

### Post by Mecasickle on 2012-03-19
I'm having the same problem but on Ubuntu 12.04 beta, did you get to fix this?

---

### Post by nothingspecial on 2012-03-20
*Thread moved to **General Help**.*

---

