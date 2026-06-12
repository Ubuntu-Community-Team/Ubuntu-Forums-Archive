---
title: "GEANT4 Installation Issues"
date: 2010-12-21
forum: General Help
---

### Post by Zaglamir on 2010-12-21
Hi all,

I've been attempting to install GEANT4 (a physics simulation program thing) however, I keep running into an issue. I've attempted to find answers within GEANT Documentation, but this seems to be experienced often by users, but not addressed within their documentation. 

Anyways, when I try to build it says I have installation errors, and the only one I can find within the output is this:

```
/usr/bin/ld: cannot find -lGLU
collect2: ld returned 1 exit status
make[2]: *** [/home/zach/geant4/geant4_9_4_b01/lib/Linux-g++/libG4FR.so] Error 1
Creating shared library /home/zach/geant4/geant4_9_4_b01/lib/Linux-g++/libG4visHepRep.so ...
/usr/bin/ld: cannot find -lGLU
collect2: ld returned 1 exit status
make[2]: *** [/home/zach/geant4/geant4_9_4_b01/lib/Linux-g++/libG4visHepRep.so] Error 1
Creating shared library /home/zach/geant4/geant4_9_4_b01/lib/Linux-g++/libG4RayTracer.so ...
/usr/bin/ld: cannot find -lGLU
collect2: ld returned 1 exit status
make[2]: *** [/home/zach/geant4/geant4_9_4_b01/lib/Linux-g++/libG4RayTracer.so] Error 1
Creating shared library /home/zach/geant4/geant4_9_4_b01/lib/Linux-g++/libG4VRML.so ...
/usr/bin/ld: cannot find -lGLU
collect2: ld returned 1 exit status
make[2]: *** [/home/zach/geant4/geant4_9_4_b01/lib/Linux-g++/libG4VRML.so] Error 1

```It's the same error over and over. "/usr/bin/ld cannot find -lGLU" where the first letter after the dash is a lowercase 'L.' It shows up a few other places in the code, followed by a different .so name. I'm using "gcc 4.4.3" which is technically a newer version than the recommended version for the install. It has also mentioned something about not being able to find OpenGL, but I have a GL folder in my /usr/bin/ now, so I think that one is fixed, and it still refuses to 'make.' 

I'm not sure what it is asking me to do inside the /usr/bin/ld folder. Do I need to add something? Do I need a different library? I'm still figuring out how this whole linux library system works and whatnot, so I'm not sure what it's asking for.

Thanks for your time,

Zach

---

### Post by Zaglamir on 2010-12-22
Bump.

---

### Post by sanjeevchs on 2011-02-27
You need to install freeglut3-dev

by typing in the terminal

sudo apt-get install freeglut3-dev

for details...

[http://conquer-ur-computer.blogspot.com/2011/02/how-to-install-geant4-in-ubuntu-linux.html](http://conquer-ur-computer.blogspot.com/2011/02/how-to-install-geant4-in-ubuntu-linux.html)

---

### Post by jalirious on 2011-03-15
Or use packages and avoid headaches;
1) sudo gedit /etc/apt/sources.list 
2) Add the lines
deb [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) stable hep
deb-src [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) stable hep
3)save, apt-get update. apt-get install geant4

For further info, click on above links. I didn't have freeglut3-dev to get it working, btw.

For reference, my system is 10.10 64-bit.

---

### Post by jalirious on 2011-03-16
PLEASE IGNORE THIS BIT. It's up for my own reference to ensure I don't chase my tail so much in the future.

sudo install-geant4-data all
then
[http://geant4.slac.stanford.edu/tutorial/installation/Geant4.9.3/Linux/Geant4_9_3_Linux_Installation.htm#_Getting_Data_Files](http://geant4.slac.stanford.edu/tutorial/installation/Geant4.9.3/Linux/Geant4_9_3_Linux_Installation.htm#_Getting_Data_Files)

Put the G4EMLOW.6.9.tar.gz in the data directory (/usr/share/geant4/data usually)
unzip, move old 'un into a trash dir.
reboot

(if you need all the low energy packages, trimmings, etc)

---

