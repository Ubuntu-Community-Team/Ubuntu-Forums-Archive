---
title: "trying to install HeeksCNC and having trouble (See Pastes from Terminal)"
date: 2012-09-08
forum: General Help
---

### Post by 777funk on 2012-09-08
I went through the steps from this instruction set:
[http://code.google.com/p/heekscad/wiki/UbuntuInstallation](http://code.google.com/p/heekscad/wiki/UbuntuInstallation)

and in the Terminal I end up with this at this step in the process:
> -- Build files have been written to: /home/nick/heekscad
nick@NickUbuntu:~/heekscad$ make package
make: *** No rule to make target `package'.  Stop.
nick@NickUbuntu:~/heekscad$ sudo dpkg -i heekscad_*.deb
[sudo] password for nick: 
dpkg: error processing heekscad_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 heekscad_*.deb


Being a new Ubuntu user, I have no idea where to look.

---

### Post by raja.genupula on 2012-09-08
```
nick@NickUbuntu:~/heekscad$ make package
make: *** No rule to make target `package'.  Stop.
```

here is the area of errors , this is the process have to be success .

---

### Post by 777funk on 2012-09-08
> **raja.genupula said:**
> ```
nick@NickUbuntu:~/heekscad$ make package
make: *** No rule to make target `package'.  Stop.
```here is the area of errors , this is the process have to be success .

I understood this but I don't know how to make it work. Any tips?

---

### Post by raja.genupula on 2012-09-08
Ok post here the total process of what you have done and what you got . Then we can help you by finding where is the exact mistake .

---

### Post by 777funk on 2012-09-08
> **raja.genupula said:**
> Ok post here the total process of what you have done and what you got . Then we can help you by finding where is the exact mistake .

Sure, here is that. Also, I believe I just followed the steps in that article (at least I tried to ).
> 
nick@NickUbuntu:~$ sudo apt-get install git subversion libwxbase2.8-dev cmake build-essential libopencascade-dev libwxgtk2.8-dev libgtkglext1-dev python-dev cmake libboost-python-dev libgtkglext1-dev python-dev cma[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cmake is already the newest version.
git is already the newest version.
subversion is already the newest version.
libgtkglext1-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base language-pack-kde-zh-hans-base amarok-help-en
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gccxml libboost-python1.46-dev libboost-python1.46.1 libboost1.46-dev libftgl2 libopencascade-foundation-6.5.0
  libopencascade-foundation-dev libopencascade-modeling-6.5.0 libopencascade-modeling-dev libopencascade-ocaf-6.5.0
  libopencascade-ocaf-dev libopencascade-ocaf-lite-6.5.0 libopencascade-ocaf-lite-dev libopencascade-visualization-6.5.0
  libopencascade-visualization-dev libssl-dev libssl-doc python2.7-dev wx-common wx2.8-headers
Suggested packages:
  libboost1.46-doc python3 libboost-date-time1.46-dev libboost-filesystem1.46-dev libboost-graph1.46-dev libboost-iostreams1.46-dev
  libboost-math1.46-dev libboost-program-options1.46-dev libboost-random1.46-dev libboost-regex1.46-dev
  libboost-serialization1.46-dev libboost-signals1.46-dev libboost-system1.46-dev libboost-test1.46-dev libboost-thread1.46-dev
  libboost-wave1.46-dev xsltproc doxygen default-jdk fop opencascade-doc wx2.8-doc
The following NEW packages will be installed:
  gccxml libboost-python-dev libboost-python1.46-dev libboost-python1.46.1 libboost1.46-dev libftgl2 libopencascade-dev
  libopencascade-foundation-6.5.0 libopencascade-foundation-dev libopencascade-modeling-6.5.0 libopencascade-modeling-dev
  libopencascade-ocaf-6.5.0 libopencascade-ocaf-dev libopencascade-ocaf-lite-6.5.0 libopencascade-ocaf-lite-dev
  libopencascade-visualization-6.5.0 libopencascade-visualization-dev libssl-dev libssl-doc libwxbase2.8-dev libwxgtk2.8-dev
  python-dev python2.7-dev wx-common wx2.8-headers
The following packages will be upgraded:
  build-essential
1 upgraded, 25 newly installed, 0 to remove and 9 not upgraded.
Need to get 75.3 MB of archives.
After this operation, 227 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main build-essential i386 11.5ubuntu2.1 [5,796 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gccxml i386 0.9.0+cvs20111013-1 [3,966 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libboost1.46-dev i386 1.46.1-7ubuntu3 [7,641 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libboost-python1.46.1 i386 1.46.1-7ubuntu3 [226 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libssl-dev i386 1.0.1-4ubuntu5.5 [1,420 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main python2.7-dev i386 2.7.3-0ubuntu3.1 [29.2 MB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main python-dev i386 2.7.3-0ubuntu2 [1,084 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libboost-python1.46-dev i386 1.46.1-7ubuntu3 [314 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libboost-python-dev i386 1.48.0.2 [3,100 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libftgl2 i386 2.1.3~rc5-4 [62.5 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libssl-doc all 1.0.1-4ubuntu5.5 [1,034 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe wx2.8-headers i386 2.8.12.1-6ubuntu2 [1,485 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libwxbase2.8-dev i386 2.8.12.1-6ubuntu2 [31.2 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe wx-common i386 2.8.12.1-6ubuntu2 [52.9 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libwxgtk2.8-dev i386 2.8.12.1-6ubuntu2 [31.5 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-foundation-6.5.0 i386 6.5.0.dfsg-2build1 [1,478 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-foundation-dev all 6.5.0.dfsg-2build1 [1,199 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-modeling-6.5.0 i386 6.5.0.dfsg-2build1 [14.5 MB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-modeling-dev all 6.5.0.dfsg-2build1 [3,479 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-ocaf-lite-6.5.0 i386 6.5.0.dfsg-2build1 [1,633 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-ocaf-lite-dev all 6.5.0.dfsg-2build1 [557 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-visualization-6.5.0 i386 6.5.0.dfsg-2build1 [4,818 kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-ocaf-6.5.0 i386 6.5.0.dfsg-2build1 [1,009 kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-ocaf-dev all 6.5.0.dfsg-2build1 [174 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-visualization-dev all 6.5.0.dfsg-2build1 [889 kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libopencascade-dev all 6.5.0.dfsg-2build1 [8,266 B]
Fetched 75.3 MB in 23min 19s (53.8 kB/s)                                       
(Reading database ... 216616 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using .../build-essential_11.5ubuntu2.1_i386.deb) ...
Unpacking replacement build-essential ...
Selecting previously unselected package gccxml.
Unpacking gccxml (from .../gccxml_0.9.0+cvs20111013-1_i386.deb) ...
Selecting previously unselected package libboost1.46-dev.
Unpacking libboost1.46-dev (from .../libboost1.46-dev_1.46.1-7ubuntu3_i386.deb) ...
Selecting previously unselected package libboost-python1.46.1.
Unpacking libboost-python1.46.1 (from .../libboost-python1.46.1_1.46.1-7ubuntu3_i386.deb) ...
Selecting previously unselected package libssl-dev.
Unpacking libssl-dev (from .../libssl-dev_1.0.1-4ubuntu5.5_i386.deb) ...
Selecting previously unselected package python2.7-dev.
Unpacking python2.7-dev (from .../python2.7-dev_2.7.3-0ubuntu3.1_i386.deb) ...
Selecting previously unselected package python-dev.
Unpacking python-dev (from .../python-dev_2.7.3-0ubuntu2_i386.deb) ...
Selecting previously unselected package libboost-python1.46-dev.
Unpacking libboost-python1.46-dev (from .../libboost-python1.46-dev_1.46.1-7ubuntu3_i386.deb) ...
Selecting previously unselected package libboost-python-dev.
Unpacking libboost-python-dev (from .../libboost-python-dev_1.48.0.2_i386.deb) ...
Selecting previously unselected package libftgl2.
Unpacking libftgl2 (from .../libftgl2_2.1.3~rc5-4_i386.deb) ...
Selecting previously unselected package libssl-doc.
Unpacking libssl-doc (from .../libssl-doc_1.0.1-4ubuntu5.5_all.deb) ...
Selecting previously unselected package wx2.8-headers.
Unpacking wx2.8-headers (from .../wx2.8-headers_2.8.12.1-6ubuntu2_i386.deb) ...
Selecting previously unselected package libwxbase2.8-dev.
Unpacking libwxbase2.8-dev (from .../libwxbase2.8-dev_2.8.12.1-6ubuntu2_i386.deb) ...
Selecting previously unselected package wx-common.
Unpacking wx-common (from .../wx-common_2.8.12.1-6ubuntu2_i386.deb) ...
Selecting previously unselected package libwxgtk2.8-dev.
Unpacking libwxgtk2.8-dev (from .../libwxgtk2.8-dev_2.8.12.1-6ubuntu2_i386.deb) ...
Selecting previously unselected package libopencascade-foundation-6.5.0.
Unpacking libopencascade-foundation-6.5.0 (from .../libopencascade-foundation-6.5.0_6.5.0.dfsg-2build1_i386.deb) ...
Selecting previously unselected package libopencascade-foundation-dev.
Unpacking libopencascade-foundation-dev (from .../libopencascade-foundation-dev_6.5.0.dfsg-2build1_all.deb) ...
Selecting previously unselected package libopencascade-modeling-6.5.0.
Unpacking libopencascade-modeling-6.5.0 (from .../libopencascade-modeling-6.5.0_6.5.0.dfsg-2build1_i386.deb) ...
Selecting previously unselected package libopencascade-modeling-dev.
Unpacking libopencascade-modeling-dev (from .../libopencascade-modeling-dev_6.5.0.dfsg-2build1_all.deb) ...
Selecting previously unselected package libopencascade-ocaf-lite-6.5.0.
Unpacking libopencascade-ocaf-lite-6.5.0 (from .../libopencascade-ocaf-lite-6.5.0_6.5.0.dfsg-2build1_i386.deb) ...
Selecting previously unselected package libopencascade-ocaf-lite-dev.
Unpacking libopencascade-ocaf-lite-dev (from .../libopencascade-ocaf-lite-dev_6.5.0.dfsg-2build1_all.deb) ...
Selecting previously unselected package libopencascade-visualization-6.5.0.
Unpacking libopencascade-visualization-6.5.0 (from .../libopencascade-visualization-6.5.0_6.5.0.dfsg-2build1_i386.deb) ...
Selecting previously unselected package libopencascade-ocaf-6.5.0.
Unpacking libopencascade-ocaf-6.5.0 (from .../libopencascade-ocaf-6.5.0_6.5.0.dfsg-2build1_i386.deb) ...
Selecting previously unselected package libopencascade-ocaf-dev.
Unpacking libopencascade-ocaf-dev (from .../libopencascade-ocaf-dev_6.5.0.dfsg-2build1_all.deb) ...
Selecting previously unselected package libopencascade-visualization-dev.
Unpacking libopencascade-visualization-dev (from .../libopencascade-visualization-dev_6.5.0.dfsg-2build1_all.deb) ...
Selecting previously unselected package libopencascade-dev.
Unpacking libopencascade-dev (from .../libopencascade-dev_6.5.0.dfsg-2build1_all.deb) ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu2.1) ...
Setting up gccxml (0.9.0+cvs20111013-1) ...
Setting up libboost1.46-dev (1.46.1-7ubuntu3) ...
Setting up libboost-python1.46.1 (1.46.1-7ubuntu3) ...
Setting up libssl-dev (1.0.1-4ubuntu5.5) ...
Setting up python2.7-dev (2.7.3-0ubuntu3.1) ...
Setting up python-dev (2.7.3-0ubuntu2) ...
Setting up libboost-python1.46-dev (1.46.1-7ubuntu3) ...
Setting up libboost-python-dev (1.48.0.2) ...
Setting up libftgl2 (2.1.3~rc5-4) ...
Setting up libssl-doc (1.0.1-4ubuntu5.5) ...
Setting up wx2.8-headers (2.8.12.1-6ubuntu2) ...
Setting up libwxbase2.8-dev (2.8.12.1-6ubuntu2) ...
update-alternatives: using /usr/lib/i386-linux-gnu/wx/config/base-unicode-release-2.8 to provide /usr/bin/wx-config (wx-config) in auto mode.
Setting up wx-common (2.8.12.1-6ubuntu2) ...
Setting up libwxgtk2.8-dev (2.8.12.1-6ubuntu2) ...
update-alternatives: using /usr/lib/i386-linux-gnu/wx/config/gtk2-unicode-release-2.8 to provide /usr/bin/wx-config (wx-config) in auto mode.
Setting up libopencascade-foundation-6.5.0 (6.5.0.dfsg-2build1) ...
Setting up libopencascade-foundation-dev (6.5.0.dfsg-2build1) ...
Setting up libopencascade-modeling-6.5.0 (6.5.0.dfsg-2build1) ...
Setting up libopencascade-modeling-dev (6.5.0.dfsg-2build1) ...
Setting up libopencascade-ocaf-lite-6.5.0 (6.5.0.dfsg-2build1) ...
Setting up libopencascade-ocaf-lite-dev (6.5.0.dfsg-2build1) ...
Setting up libopencascade-visualization-6.5.0 (6.5.0.dfsg-2build1) ...
Setting up libopencascade-ocaf-6.5.0 (6.5.0.dfsg-2build1) ...
Setting up libopencascade-ocaf-dev (6.5.0.dfsg-2build1) ...
Setting up libopencascade-visualization-dev (6.5.0.dfsg-2build1) ...
Setting up libopencascade-dev (6.5.0.dfsg-2build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
nick@NickUbuntu:~$ git clone --recursive git://github.com/Heeks/heekscad.git
fatal: destination path 'heekscad' already exists and is not an empty directory.
nick@NickUbuntu:~$ cd heekscad
nick@NickUbuntu:~/heekscad$ cmake .
-- Found wxWidgets: TRUE 
CMake Warning at CMakeLists.txt:26 (find_package):
  Could not find module FindOCE.cmake or a configuration file for package
  OCE.

  Adjust CMAKE_MODULE_PATH to find FindOCE.cmake or set OCE_DIR to the
  directory containing a CMake configuration file for OCE.  The file will
  have one of the following names:

    OCEConfig.cmake
    oce-config.cmake



-- Found OCC include dir: /usr/include/opencascade
-- Found OCC lib dir: /usr/lib
-- This is a 32-bit system.
-- Found PythonLibs: /usr/lib/libpython2.7.so 
-- Looking for XOpenDisplay in /usr/lib/i386-linux-gnu/libX11.so;/usr/lib/i386-linux-gnu/libXext.so
-- Looking for XOpenDisplay in /usr/lib/i386-linux-gnu/libX11.so;/usr/lib/i386-linux-gnu/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/i386-linux-gnu/libX11.so
-- Found OpenGL: /usr/lib/i386-linux-gnu/libGL.so 
-- Configuring done
CMake Error at src/CMakeLists.txt:340 (add_executable):
  Cannot find source file:

    ../libarea/Arc.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .m .M .mm .h .hh .h++ .hm .hpp
  .hxx .in .txx


-- Build files have been written to: /home/nick/heekscad
nick@NickUbuntu:~/heekscad$ make package
make: *** No rule to make target `package'.  Stop.
nick@NickUbuntu:~/heekscad$ sudo dpkg -i heekscad_*.deb
[sudo] password for nick: 
dpkg: error processing heekscad_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 heekscad_*.deb
nick@NickUbuntu:~/heekscad$ sudo dpkg -i heekscad_*.deb
dpkg: error processing heekscad_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 heekscad_*.deb


---

### Post by 777funk on 2012-09-08
Any ideas? I'd love to get this working.

---

### Post by steeldriver on 2012-09-08
I downloaded it and tried to build it just to see if I could help - basically it appears to be broken, the cmake never generates a makefile (due to the initial FindOCE.cmake error, I think)

I poked around a bit and found an updated INSTALL_UBUNTU.sh script which the author claimed had fixed the FindOCE.cmake error - but that seemed to be even more broken (didn't even download the source - I tried it again after manually grabbing the git clone and it still failed). Here it is anyway - ymmv

[https://github.com/Heeks/heekscad/pull/11](https://github.com/Heeks/heekscad/pull/11)

---

### Post by 777funk on 2012-09-08
> **steeldriver said:**
> I downloaded it and tried to build it just to see if I could help - basically it appears to be broken, the cmake never generates a makefile (due to the initial FindOCE.cmake error, I think)

I poked around a bit and found an updated INSTALL_UBUNTU.sh script which the author claimed had fixed the FindOCE.cmake error - but that seemed to be even more broken (didn't even download the source - I tried it again after manually grabbing the git clone and it still failed). Here it is anyway - ymmv

[https://github.com/Heeks/heekscad/pull/11](https://github.com/Heeks/heekscad/pull/11)

Thanks Steel! I appreciate you always helping me find what's wrong with these elusive drivers. Still no sound from that Recording Input device or GCode from my DXF drawings but I'm not giving up yet!!! And I still have a dual boot for the time being.

---

### Post by hugies1 on 2012-09-15
I was just trying to install just now and ran into the same problem also.

A quick read of the installation instructions revealed some dependencies that I was missing which were not explicitly mentioned in the wiki. From your terminal record you are missing this also. You will need to pull the git depository from various sources first on top of heekscad. Follow my instructions instead. 

Run the following from terminal in order:

sudo apt-get install libopencascade-foundation-6.5.0 libopencascade-modeling-6.5.0 python-wxgtk2.8 libboost-python1.48.0 git subversion cmake build-essential 
git clone git://github.com/Heeks/heekscad.git
git clone git://github.com/Heeks/heekscnc.git
git clone git://github.com/Heeks/libarea.git
git clone git://github.com/aewallin/opencamlib.git
git clone git://github.com/tpaviot/oce.git
cd heekscad
cmake ./
make
sudo make install

this seems to work for me

---

### Post by 777funk on 2012-09-16
> **hugies1 said:**
> I was just trying to install just now and ran into the same problem also.

A quick read of the installation instructions revealed some dependencies that I was missing which were not explicitly mentioned in the wiki. From your terminal record you are missing this also. You will need to pull the git depository from various sources first on top of heekscad. Follow my instructions instead. 

Run the following from terminal in order:

sudo apt-get install libopencascade-foundation-6.5.0 libopencascade-modeling-6.5.0 python-wxgtk2.8 libboost-python1.48.0 git subversion cmake build-essential 
git clone git://github.com/Heeks/heekscad.git
git clone git://github.com/Heeks/heekscnc.git
git clone git://github.com/Heeks/libarea.git
git clone git://github.com/aewallin/opencamlib.git
git clone git://github.com/tpaviot/oce.git
cd heekscad
cmake ./
make
sudo make install

this seems to work for me


This worked until:
> nick@NickUbuntu:~/heekscad$ make
make: *** No targets specified and no makefile found.  Stop.
nick@NickUbuntu:~/heekscad$ 

then this next line did this:
> nick@NickUbuntu:~/heekscad$ sudo make install
[sudo] password for nick: 
make: *** No rule to make target `install'.  Stop.

---

### Post by panchula on 2012-09-17
I' trying to install Heeks on 12.04 x64 and am getting the following:

make[2]: *** No rule to make target `/usr/lib/libXmu.so', needed by `bin/heekscad-0.22.0'.  Stop.

Any ideas on how to fix this?

-Mike

---

### Post by slaith on 2013-04-19
Hello

Fist post on ubuntu forum.

I realise that this is an old one, but I haven't seen anyone getting around this.

I managed to get around this error by actually just copying a directory from on place to another.

The site I was going from was this one.
[http://code.google.com/p/heekscad/wiki/BuildWithCmakeOnUbuntu](http://code.google.com/p/heekscad/wiki/BuildWithCmakeOnUbuntu)

I noticed that the script is looking for the libarea/Arc.cpp file.
So since I had already run the entire script I found the Arc.cpp file in the heeksCNC/libarea directory.
I figured that maybe the directory trees should resemble one another so I just copied the whole libarea folder from heeksCAD/heeksCNC/ to the heeksCAD.
Then I just ran the command
make ./
and it never complained.
So then I made the package and installed as per the instructions.

Hopefully this will help some poor soul out there. :D

Have a good weekend 

Patrik

---

### Post by duesentriebchen on 2013-06-02
Hy there.I managed to install HeeksCAD and HeeksCNC on K/Ubuntu 10.04, 12.04 and 13.04 with one script.Take a look at it [https://elrippoisland.net/public/CAD_CAM/cam.html](https://elrippoisland.net/public/CAD_CAM/cam.html)Have a nice week at work.

---

### Post by Brad wilkinson on 2013-10-31
Trying to install the HeeksCAD and HeeksCam software, and having some problems.

I think they start with the build looking for "libboost-python1.40.0" when I have "libboost-python1.46.1" loaded on my system according to synaptic.

I have no idea how to load a previous version of the libboost-python module (or how to update the makefile to use the later libboost), so can anyone help?

also - here is the whole terminal output - 

> bradley@Ubuntu-desktop:~/heekscad$ ./INSTALL_UBUNTU.sh
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release.gpg                                                                                                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release.gpg                                                                                                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release                                                                                                                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release                                                                                                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release                                                                                                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Sources                                                                                                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Sources                                                                                                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Sources                                                                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Sources                                                                                                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main amd64 Packages                                                                                                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted amd64 Packages                                                                                                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe amd64 Packages                                                                                                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse amd64 Packages                                                                                                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main i386 Packages                                                                                                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted i386 Packages                                                                                                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe i386 Packages                                                                                                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse i386 Packages                                                                                                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main TranslationIndex                                                                                                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                                                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted TranslationIndex                                                                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe TranslationIndex                                                                                                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Sources                                                                                                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Sources                                                                                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Sources                                                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Sources                                                                                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main amd64 Packages                                                                                              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted amd64 Packages                                                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe amd64 Packages                                                               
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg                                                                                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse amd64 Packages                                                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main i386 Packages                                              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted i386 Packages                                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe i386 Packages                                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse i386 Packages                                                              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main TranslationIndex                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main amd64 Packages                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted amd64 Packages                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe amd64 Packages                                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse amd64 Packages                                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main i386 Packages                                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted i386 Packages                                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe i386 Packages                                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main TranslationIndex                                                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en_AU                                                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en                                                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en_AU                                            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en                                                                                
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise Release.gpg                                                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en_AU                                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en                                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Translation-en                                                 
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Translation-en_AU                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Translation-en                                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Translation-en_AU                                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Translation-en                                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Translation-en_AU                                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Translation-en                                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Translation-en                                                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main Translation-en                                                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse Translation-en                                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted Translation-en                                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe Translation-en                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                 
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                                                           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                        
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise Release                                                                                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                               
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main amd64 Packages                                                                                        
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                                      
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main i386 Packages                                                                             
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main TranslationIndex                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                             
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                                                  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [92.1 kB]                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam TranslationIndex                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [29.3 kB]                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,804 B]                                                          
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [334 kB]                                                                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en_AU                                                                                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en                                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_AU                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                     
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_AU              
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]                                                                               
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [84.0 kB]                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                                            
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,449 B]                                                                              
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [353 kB]                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                                            
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]                                                                               
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [87.9 kB]                                                                                 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,640 B]                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                                                                             
Fetched 1,048 kB in 10s (97.4 kB/s)                                                                                                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libwxgtk2.8-dbg' for regex 'libwxgtk2.8'
Note, selecting 'libwxgtk2.8-dev' for regex 'libwxgtk2.8'
Note, selecting 'libwxgtk2.8-0' for regex 'libwxgtk2.8'
E: Unable to locate package libboost-python1.49.0
E: Couldn't find any package by regex 'libboost-python1.49.0'
CMake Warning at CMakeLists.txt:26 (find_package):
  Could not find module FindOCE.cmake or a configuration file for package
  OCE.

  Adjust CMAKE_MODULE_PATH to find FindOCE.cmake or set OCE_DIR to the
  directory containing a CMake configuration file for OCE.  The file will
  have one of the following names:

    OCEConfig.cmake
    oce-config.cmake



-- Configuring done
CMake Error at src/CMakeLists.txt:340 (add_executable):
  Cannot find source file:

    ../libarea/Arc.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .m .M .mm .h .hh .h++ .hm .hpp
  .hxx .in .txx


-- Build files have been written to: /home/bradley/heekscad
make: *** No rule to make target `package'.  Stop.
Selecting previously unselected package heekscad.
(Reading database ... 625198 files and directories currently installed.)
Unpacking heekscad (from heekscad_beta-0.18.1_amd64.deb) ...
dpkg: dependency problems prevent configuration of heekscad:
 heekscad depends on libboost-python1.40.0 | libboost-python1.42.0; however:
  Package libboost-python1.40.0 is not installed.
  Package libboost-python1.42.0 is not installed.
dpkg: error processing heekscad (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 heekscad
./INSTALL_UBUNTU.sh: 20: cd: can't cd to /home/bradley/heekscad/heekscnc/
CMake Warning at CMakeLists.txt:26 (find_package):
  Could not find module FindOCE.cmake or a configuration file for package
  OCE.

  Adjust CMAKE_MODULE_PATH to find FindOCE.cmake or set OCE_DIR to the
  directory containing a CMake configuration file for OCE.  The file will
  have one of the following names:

    OCEConfig.cmake
    oce-config.cmake



-- Configuring done
CMake Error at src/CMakeLists.txt:340 (add_executable):
  Cannot find source file:

    ../libarea/Arc.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .m .M .mm .h .hh .h++ .hm .hpp
  .hxx .in .txx


-- Build files have been written to: /home/bradley/heekscad
make: *** No rule to make target `package'.  Stop.
Selecting previously unselected package heekscnc.
(Reading database ... 625389 files and directories currently installed.)
Unpacking heekscnc (from heekscnc_beta-0.18.1_amd64.deb) ...
dpkg: dependency problems prevent configuration of heekscnc:
 heekscnc depends on libboost-python1.40.0 | libboost-python1.42.0; however:
  Package libboost-python1.40.0 is not installed.
  Package libboost-python1.42.0 is not installed.
dpkg: error processing heekscnc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 heekscnc
./INSTALL_UBUNTU.sh: 28: cd: can't cd to /home/bradley/heekscad/heekscnc/libarea/
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
ln: failed to create symbolic link `/home/bradley/heekscad/heekscnc/area.so': No such file or directory
bradley@Ubuntu-desktop:~/heekscad$ 


---

### Post by Brad wilkinson on 2013-11-04
So I have been digging further and trying to get HeeksCNC to work, but I keep ending up with a broken package (unfulfilled requirement) sort of error.

As i read throug the make process in the terminal, I get the following error message as it trys to install the HeeksCNC add on:

> dpkg: dependency problems prevent configuration of heekscnc:
 heekscnc depends on libboost-python1.40.0 | libboost-python1.42.0 | libboost-python1.49.0; however:
  Package libboost-python1.40.0 is not installed.
  Package libboost-python1.42.0 is not installed.
  Package libboost-python1.49.0 is not installed.

But at the moment in the official ubuntu repo's we have:

libboost-python1.46.1
libboost-python1.48.0

So how do I get (I assume) one of the versions required on my system, or do I need to change the cMake file for HeeksCNC (to reference one of the libboost files available in the repo) or am I barking up the completely wrong tree?

---

