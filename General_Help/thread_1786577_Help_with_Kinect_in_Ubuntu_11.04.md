---
title: "Help with Kinect in Ubuntu 11.04"
date: 2011-06-19
forum: General Help
---

### Post by thomas515 on 2011-06-19
I've seen many demos online of kinect interfacing with Linux.  I can't find any downloads just videos of of programs running.  Anyone know of a download. Thanks.

---

### Post by DanneStrat on 2011-06-20
> **thomas515 said:**
> I've seen many demos online of kinect interfacing with Linux.  I can't find any downloads just videos of of programs running.  Anyone know of a download. Thanks.

There's some steps involved but these instructions should help you get started.

Some download links were broken in the original guide I found so I fixed them. The version numbers of the packages may also differ from the original guide so you may have to modify the commands used accordingly. Here you go:

```
GUIDE FOR INSTALLING OPENNI DRIVERS FOR KINECT ON LINUX 
-Ibrahim Musba 
I have done the installation on both 64 bit as well as 32 bit Linux 
and had no serious problems as such. 
I would recommend Ubuntu 10.10 or greater. I had done it on Ubuntu 
11.04 

STEP 1 
------ 
The  links below will direct you to the latest unstable versions 
Download the files appropriate for your operating system (ubuntu 10.10 packages for 11.04)
1. http://www.openni.org/downloadfiles/opennimodules/openni-binaries/20-latest-unstable 
2. http://www.openni.org/downloadfiles/opennimodules/openni-compliant-middleware-binaries/33-latest-unstable 
3. http://www.openni.org/downloadfiles/opennimodules/openni-compliant-hardware-binaries/31-latest-unstable

Make a new folder called kinect 
$ cd 
$ mkdir kinect 
$ cd kinect 
and extract the downloaded files into it. 

STEP 2 
------ 
Update your linux 
$ sudo apt-get update 
install these files which are necessary for proper installation of 
drivers 
$ sudo apt-get install mono-complete 
$ sudo apt-get install libusb-1.0-0-dev 
$ sudo apt-get install freeglut3-dev 

STEP 3 
------ 
The extracted folders in step 1 will be 
->OpenNI-Bin-Linux32-v1.1.0.41 
->Sensor-Bin-Linux32-v5.0.1.32 
->Nite-1.3.1.5 
rename it to OpenNI, Sensor, Nite respectively 
Download the folder SensorKinect from https://github.com/avin2/SensorKinect 
to the kinect folder (You only need to click on "downloads" and you will get the right folder) 
extract and rename the foler to SensorKinect 

STEP 4 
------ 
Go to the folder OpenNI, Sensor, Nite and run sudo ./install.sh 
$ cd 
$ cd kinect 
$ cd OpenNI 
$ sudo ./install.sh 
$ cd ../Sensor 
$ sudo ./install.sh 
$ cd ../Nite 
$ sudo ./install.sh 
Use this license when asked during the installation: 
0KOIk2JeIBYClPWVnMoRKn5cdY4= 
$ cd ../SensorKinect/Platform/Linux-x86/CreateRedist/ 
$ sudo ./RedistMaker 
$ cd ../Redist 
$ sudo ./install.sh 
You should be done by now. In case of any confusion refer the README 
in SensorKinect folder. 

STEP 5 
------ 
Testing if everything is working fine 
Connect you kinect and run the samples from the OpenNI folder 
$ cd ~/kinect/OpenNI/Samples/Bin/Release/ 
(assuming the kinect folder is in home folder, otherwise go to the 
respective folder) 
$ ./NiViewer 
You should get the depth map and image stream on your window. 
--DONE-- 
```

Original post:

[http://groups.google.com/group/openni-dev/browse_thread/thread/2af8d0200892629c?pli=1](http://groups.google.com/group/openni-dev/browse_thread/thread/2af8d0200892629c?pli=1)

Good luck!

---

### Post by thomas515 on 2011-06-21
Something went wrong in the third to last step.  the ```
$ sudo ./RedistMaker
``` command. When I tried to change to the Redist directory it says it doesn't exist. I looked back at the previous step and I saw this ```
/usr/bin/ld: cannot find -lOpenNI
collect2: ld returned 1 exit status
make[1]: *** [../../Bin/Release/libXnCore.so] Error 1
make[1]: Leaving directory `/home/max/kinect/SensorKinect/Platform/Linux-x86/Build/XnCore'
make: *** [XnCore] Error 2
make: Leaving directory `/home/max/kinect/SensorKinect/Platform/Linux-x86/Build'
```. I have no idea what those errors are or how to fix them.  Everything worked great up until that last step. Any ideas would be greatly appreciated.

---

