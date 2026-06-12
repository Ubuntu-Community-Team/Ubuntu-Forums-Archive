---
title: "Geant4.9.5 on 12.04"
date: 2012-04-27
forum: General Help
---

### Post by jalirious on 2012-04-27
Well, I'm listing here my efforts to install the new version of geant4 on the new version of ubuntu (64 bit). Gnome-fallback.

The G4wizards have decided in their wisdom to change the familiar installation script method completely, now all options have to be set as an input to cmake. 

Ok, so what do we have here?
cmake = 2.8.6
gcc = Ubuntu/Linaro 4.6.3-1ubuntu5
g++ = Ubuntu/Linaro 4.6.3-1ubuntu5
Got rid of all mention of CLHEP / geant in the environmental variables (this version includes it - which is nice)

If you're daft enough to try to follow this, then check the following commands draw a blank
printenv | grep G4
printenv | grep CLHEP

I installed all the bits mentioned here [http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch02s03.html]("http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch02s03.html")

Then decided to enable all the visualisation hijinx, as before I had problems with the raytracer wotsit.

cmake -DCMAKE_INSTALL_PREFIX=/home/bp/geant4/geant4.9.5-install -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_GDML=ON -DGEANT4_USE_QT=ON -DGEANT4_USE_OPENGL_X11=ON /home/bp/geant4/geant4.9.5

(here the first directory you create where to install geant, the second is for the unzipped dir)

cmake was ok, then make -j4 (as I have four processors) .. tick tock..

---

### Post by jalirious on 2012-04-27
So, after setting G4INSTALL, G4LIB and G4SYSTEM in bashrc, I make some code..

Compiling blah.cc ...
Using granular libraries ...
ERROR: No liblist program or library map file.
       These are needed for building with granular
       libraries.
         cd $G4INSTALL/source
         gmake
       or if you are sure you have already made all the
       granular libraries:
         gmake libmap
make: *** [bin/Linux-g++/blah] Error 1

So, I do this gmake libmap, make clean, make..
Using granular libraries ...
Linking exampleN03
/usr/bin/ld: cannot find -lG4digits
/usr/bin/ld: cannot find -lG4hits
/usr/bin/ld: cannot find -lG4ev... (etc, etc)

Any bones to throw?

---

### Post by jalirious on 2012-04-30
. ~/geant4/geant-install/share/Geant4-9.5.0/geant4make/geant4make.sh

---

### Post by jalirious on 2012-05-05
Well, you swines, I finally installed a standalone vrml97 viewer on 12.04 64bit.

Firstly install (all hardy packages) like this

libmozjs0d
(Version libmozjs0d 1.8.1.18+nobinonly.b308.cvs20090331t155113-0ubuntu0.8.04.1)

Then
libopenvrml5c2a
(Version libopenvrml5c2a 0.15.10-9ubuntu1)

Then
openvrml-lookat
(Version openvrml-lookat 0.15.10-9ubuntu1)

command 'lookat g4_00.wrl'

(This also works on 10.04 64)

---

### Post by faizlo on 2012-05-07
Hi,

I dont know if you had any luck installing it, but I could install it on a Dell Optiplex 740 Machine.

When I compiled example N02, the compilation went fine with no errors. when I fire "exampleN02" from the command line, I get G4UI window (OPENGLQT - as I have used all visualizations flags passed to cmake!)
Now if I try "exampleN02 vis.mac" I get a "Segmentation fault" which I have no idea why or where does it come from?

In the G4UI I can give my /vis/ commands and I could see the beam of particles passing through the 6 pieces detectors. but I cannot get Idle> on the command line.

Same thing happened to me when I tried A01 example (which I compiled first)
Again all compilation went fine, but I get a SIG fault once I pass any of the vis.mac files to it. And I never get Idle> on the command line :(

I wonder if you can have some feedback?

best regards.

---

### Post by jalirious on 2012-05-07
Hi Faizlo.

I can now run fine (G4.9.5, 12.04), and view alright too, if a little oldskool with lookat.

To test I just compiled the (novice) Examples. I get this error:

"/home/username/geant4/geant-install/include/Geant4/G4UIQt.hh:40:21: fatal error: qobject.h: No such file or directory"

Well - in my case I don't need it as my personal code runs okay without. So, I suggest running cmake without it set as I mention above. 

(you will know this, but if anyone else is trying to install the new geant, it is neater to do this)
cd ~
mkdir geant4
cd geant4
mv ~/Downloads/geant4.9.5.tar.gz .
tar xvf geant4.9.5.tar.gz
mkdir geant4-build
mkdir geant4-install
cd geant4-build
cmake -DCMAKE_INSTALL_PREFIX=/yourpath/geant4-install -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_GDML=ON -DGEANT4_USE_QT=ON -DGEANT4_USE_OPENGL_X11=ON /yourpath/geant4.9.5

If you want some test code, pm me.

Later

---

### Post by faizlo on 2012-05-08
Hi,

I have pm'ed you and I hope ou could see the message.

Well, if you have a test code that I can use to make sure my installation is working right, I will be gas to test it.

Thanks

---

### Post by faizlo on 2012-05-10
OK!

It seems I have solved all my troubles with geant4.9.5.p01. I have also added OpenInventor to the set of my visualisations. I also have compiled many of the examples without errors (nor warnings!) so I guess I am all set now.
I also have Geant4.9.4.p04 installed on my machine - from a previous try. I plan to keep it for a while just in case.

I can confirm now that Geant4.9.5.p01 and Geant4.9.4.p04 can compile and run on Ubuntu.

---

### Post by jalirious on 2012-05-10
Nice work! Perhaps listing the steps you took might be useful? Ben.

---

### Post by vincentof on 2012-05-14
Hi to everyone
jalirious:
Did you already add: 

> if [ -f /usr/local/share/Geant4-9.5.1/geant4make/geant4make.sh ]; then
    source /usr/local/share/Geant4-9.5.1/geant4make/geant4make.sh
fito your bashrc file, so it can find geant4make.sh and some things related to libraries?
  Vladimir

---

### Post by jalirious on 2012-05-18
Yep :)

---

### Post by mac00 on 2012-09-13
Hello Every one i am using Geant4 for my task.i am new in it i want to know taht how we can save our data when we use /run/beam On command then some numerical number display i want to save them in a file if any body get me reply me.

---

