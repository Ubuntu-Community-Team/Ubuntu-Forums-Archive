---
title: "What to install to avoid 'cannot find -lGL' error on 12.04"
date: 2012-05-29
forum: General Help
---

### Post by mjsilverstri on 2012-05-29
Hi,

I am trying to build andriod source code on ubuntu 12.04. I have instealled 
$ sudo apt-get install libgl1-mesa-dev
and
 sudo apt-get install libglu1-mesa-dev

I am failing with this error:

Install: out/host/linux-x86/bin/usbtest
host Prebuilt: ddmlib-prebuilt (out/host/common/obj/JAVA_LIBRARIES/ddmlib-prebuilt_intermediates/ddmlib-prebuilt.jar)
Install: out/host/linux-x86/framework/junit.jar
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/triangleCM_intermediates/triangleCM] Error 1
make: *** Waiting for unfinished jobs....
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/triangleV2_intermediates/triangleV2] Error 1

---

### Post by gnusci on 2012-05-29
sudo apt-get install freeglut3-dev

---

### Post by mjsilverstri on 2012-05-30
Thanks. But I still get 

/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status

Any idea what else I need to do?

---

### Post by singmajesty on 2012-06-14
You can install libgl1-mesa-dev:i386 and libglu1-mesa-dev:i386, but unfortunately 12.04 doesn't allow the x86 and x64 packages to be installed at once, which is a huge pain when you are trying to do both kinds of builds on the same machine.

---

