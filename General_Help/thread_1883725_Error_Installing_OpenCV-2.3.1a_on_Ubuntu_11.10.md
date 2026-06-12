---
title: "Error Installing OpenCV-2.3.1a on Ubuntu 11.10"
date: 2011-11-19
forum: General Help
---

### Post by OtagoHarbour on 2011-11-19
I am using Ubuntu 11.10 and am trying to install OpenCV-2.3.1a.  I go through the folloing sequence after downloading and unzipping OpenCV-2.3.1a.tar.bz2.

```

cd
tar -xvf OpenCV-2.3.1a.tar
sudo svn co https://code.ros.org/svn/opencv/trunk
mkdir MakeFileDir
cd MakeFileDir
sudo cmake ../OpenCV-2.3.1
make

```This starts building OpenCV but when it is 20% done, it crashes with the following error message.

```

make[2]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_ffmpeg.o] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2

```I did a search on-line and a patch was suggested [here]("https://code.ros.org/trac/opencv/attachment/ticket/1020/ffmpeg_build.patch").  However there are two problems with this.


[LIST]
[*]There is no src directory under ~/MakeFileDir/modules/highgui/
[*]I found a src directory under ~/OpenCV-2.3.1/modules/highgui/ but its version of cap_ffmpeg.cpp did not contain any of the code that the fix said I was supposed to change.  E.g. it did not have "== enc->codec_type && video_stream < 0) {"
[/LIST]


Any assistance with resolving this problem would be greatly appreciated.
Peter.

---

