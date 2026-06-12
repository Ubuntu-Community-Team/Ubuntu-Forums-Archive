---
title: "Error running hvOpenCV (handvu-beta3 + OpenCV 2.1.0 + Ubuntu 10.04)"
date: 2010-05-26
forum: General Help
---

### Post by AdagioParaCuerdas on 2010-05-26
I have downloaded **HandVu** from Moves Institute, that is [handvu-beta3.tar.gz]("http://www.movesinstitute.org/~kolsch/HandVu/handvu-beta3.tar.gz").

After extracted I got handvu-beta3 directory. Then I compiled it on
Ubuntu following [**instructions on Ubuntu Forums**]("http://ubuntuforums.orgshowthread.php?t=981398").

I am using **OpenCV 2.1** downloaded from SourceForge that is [**OpenCV-2.1.0.tar.bz2**]("http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.1/ OpenCV-2.1.0.tar.bz2/download").

This is the current version as indicated on Oficial OpenCV web on
[**Willow Garage**]("http://opencv.willowgarage.com/wiki/")

Inside handvu-beta3 there is ***hv_OpenCV*** directory and these files are
located there:

[LIST]
[*]hvOpenCV
[*]hv_OpenCV.cpp
[*]hv_OpenCV.o
[*]hv_OpenCV.vcproj
[*]Makefile
[*]Makefile.am
[*]Makefile.in
[/LIST]

When I execute this command: **./hvOpenCV 0**

This is the output:

> will load conductor from file:
0
Hot keys:
        ESC - quit the program
        r - restart the tracking
        0-3 - set the overlay (verbosity) level
use the mouse to select the initial detection area
error with file 0:
could not find or open file
error with file 0:
could not find or open file
note: paths in VisionConductor files are relative;
in this case to /media/Files/files/downloads/web/OpenCV/HandVu/handvu-
beta3/hv_OpenCV
OpenCV Error: Unspecified error (error with file 0:
could not find or open file
note: paths in VisionConductor files are relative;
in this case to /media/Files/files/downloads/web/OpenCV/HandVu/handvu-
beta3/hv_OpenCV) in hvLoadConductor, file HandVu_Cintf.cpp, line 161
terminate called after throwing an instance of 'cv::Exception'
Aborted

Could anyone help me?

---

### Post by AdagioParaCuerdas on 2010-05-27
needed to execute

$./hvOpenCV ../config/default.conductor

:)

---

### Post by Om.Ethcelon on 2011-04-04
I tried that 
here is the output :


om@Slycon:~$ $./hvOpenCV ../config/default.conductor
bash: $./hvOpenCV: No such file or directory

---

