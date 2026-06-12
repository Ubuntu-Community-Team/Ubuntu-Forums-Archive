---
title: "Installing OpenNI (kinect) and run it with OpenCV and/or Matlab"
date: 2011-12-15
forum: General Help
---

### Post by Weg7DeY8zT on 2011-12-15
Here an instruction howto install OpenNi and to combine it with OpenCV and call it from Matlab.

Tested on a 32 bit Linux! If you are running a 64 bit version you will change part one.

[SIZE=3]1) Install OpenNi, Nite and SensorKinect[/SIZE]
```

#!/bin/sh

# Install required packages: 
apt-get install g++ libglut3-dev libboost-all-dev
apt-get install libwxbase2.8-dev libwxgtk2.8-dev wx-common

# prepare direcotry
mkdir ~/kinect
cd ~/kinect

# get openni
mkdir OpenNI
cd OpenNI
wget http://www.greenfoot.org/doc/kinect/OpenNI-Linux32.tar.bz2
tar -jxf OpenNI-Linux32.tar.bz2
sudo ./install.sh
cd ..

# install NITE
mkdir NITE
cd NITE
wget http://www.greenfoot.org/doc/kinect/NITE-Linux32.tar.bz2
tar -jxf NITE-Linux32.tar.bz2
echo '0KOIk2JeIBYClPWVnMoRKn5cdY4=' | sudo ./install.sh
cd ..

# install kinect driver
mkdir Kinect
cd Kinect
wget http://www.greenfoot.org/doc/kinect/SensorKinect-Linux32.tar.bz2
tar -jxf SensorKinect-Linux32.tar.bz2
sudo ./install.sh
cd ..


# test the installation
cd OpenNI/Samples/Bin/Release/
./Sample-NiUserTracker
cd ../../../../

```Paste this code into a file install_kinect.sh and run
```

sudo sh install_kinect.sh

```[SIZE=3]2) Install OpenCv and QT[/SIZE]
```

sudo apt-get install harpia qtcreator

```or download and make it. [http://opencv.willowgarage.com/wiki/InstallGuide](http://opencv.willowgarage.com/wiki/InstallGuide)

QtCreator is just needed if you want to compile with QT support and extend the sample code.

[SIZE=3]3) Download the C++ wrapper functions and copy it into a folder[/SIZE]
[http://svn.comiendolimones.com/OpencvKinect/](http://svn.comiendolimones.com/OpencvKinect/)

[SIZE=3]4) Create a file called makefile and paste this code into it[/SIZE]
```

OSTYPE := $(shell uname -s)

BIN_DIR = .

INC_DIRS =  /usr/include/ni

SRC_FILES = *.cpp

EXE_NAME = 3DFace_Trial

ifeq ("$(OSTYPE)","Darwin")
    LDFLAGS += -framework OpenGL -framework GLUT
else
    USED_LIBS += glut cxcore cv highgui cvaux ml QtGui QtCore pthread
endif

USED_LIBS += OpenNI


CFLAGS        = -pipe -O2 -I/usr/local/include/opencv  -D_REENTRANT $(DEFINES)
CXXFLAGS      = -pipe -O2 -I/usr/local/include/opencv  -D_REENTRANT $(DEFINES)

### COMMON MAKE FILE
include  /opt/kinect/OpenNI/Samples/Build/Common/CommonCppMakefile

```[SIZE=3]5) Move the ~/kinect folder to /opt/[/SIZE]
```

sudo mv ~/kinect  /opt/

```[SIZE=3]6) Open a Terminal and cd into the folder with the files and execute[/SIZE]
```

make

```the binaries will be written into  the Release folder

[SIZE=3]7) Enable Matlab Wrapper[/SIZE]
[https://sites.google.com/site/ujwalbonde/kinect_installation.pdf?attredirects=0](https://sites.google.com/site/ujwalbonde/kinect_installation.pdf?attredirects=0)


I hope this helps someone

---

