---
title: "OpenFrameworks in ubuntu 12.04"
date: 2012-09-27
forum: General Help
---

### Post by rasmus91 on 2012-09-27
Hi.

I am looking to make OpenFrameworks work. I have a 64 bit system, and when i run the official scripts that should install the system i get a ton of error messages, so i decided to manually install the libs, that shouldnt be too hard with synaptics, right? wrong. for some reason i can install absolutely squat of the libs i need. I've had some problems installing some things like kdenlive for some time. its typically some "lib depends on someOtherLib but it is not going to be installed" and im mostly like; "why the hell not?" 

Its the same with this libglu1-mesa-dev that i need to install, and weirdly enough the lib it depends on seems to be installed.

Any help with getting OpenFrameworks running properly will be much appreciatet, as we need to use it at school some time today. (our instructors guide did not work at all)

and also, how can i install OpenCV? googled it, but could not find a working option.

thanks.

---

### Post by rasmus91 on 2012-10-01
So i figured out how to do it, i have however run into some problems that i cant quite figure out how to solve; dependencies for OpenCV to function, for an example libgtk2.0-dev

this is what i get:
```
sudo apt-get install libgtk2.0-dev
[sudo] password for rasmus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk2.0-dev : Depends: libgtk2.0-0 (= 2.24.8-0ubuntu4) but 2.24.10-0ubuntu6 is to be installed
                 Depends: libglib2.0-dev (>= 2.27.3) but it is not going to be installed
                 Depends: libgdk-pixbuf2.0-dev (>= 2.21.0) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.29.2) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
                 Depends: libxext-dev (>= 1:1.0.1-2) but it is not going to be installed
                 Depends: libxinerama-dev (>= 1:1.0.1-4.1) but it is not going to be installed
                 Depends: libxi-dev (>= 1:1.0.1-4) but it is not going to be installed
                 Depends: libxrandr-dev (>= 1:1.2.99) but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev (>= 1:3.0.0-3) but it is not going to be installed
                 Depends: libxcomposite-dev (>= 1:0.2.0-3) but it is not going to be installed
                 Depends: libxdamage-dev (>= 1:1.0.1-3) but it is not going to be installed
                 Recommends: debhelper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

any insight?

---

