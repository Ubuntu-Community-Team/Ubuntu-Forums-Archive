---
title: "Problem installing OpenCV 2.2.0 in Ubuntu 11.04"
date: 2011-06-02
forum: General Help
---

### Post by ratatouille on 2011-06-02
Hi,

I have just installed** ubuntu 11.04 **but I am unable to install **OpenCV 2.2.0.**

I followed the steps from  [http://opencv.willowgarage.com/wiki/InstallGuide](http://opencv.willowgarage.com/wiki/InstallGuide)
I downloaded openCV 2.2.0 from  [here.]("http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.2/")

Things were fine till the **cmake** command. But after that when I run the **make** command it compiles 75-80% and the showed this error- 
> 
Linking CXX executable ../../bin/opencv_createsamples ../../lib/libopencv_highgui.so.2.2.0: undefined reference to `cvCreateCameraCapture_V4L(int)' collect2: ld returned 1 exit status make[2]: *** [bin/opencv_createsamples] Error 1 make[1]: *** [modules/haartraining/CMakeFiles/opencv_createsamples.dir/all] Error 2 make: *** [all] Error 2

I also tried the steps at [http://tech.groups.yahoo.com/group/OpenCV/message/79758](http://tech.groups.yahoo.com/group/OpenCV/message/79758) but it did not help.

Is there any neat way to install it??

---

### Post by ratatouille on 2011-06-02
Anyway it is solved now.

some made some changes in the source code. visit  [https://code.ros.org/trac/opencv/changeset/5206](https://code.ros.org/trac/opencv/changeset/5206).

Thanks,
ratatouille

---

