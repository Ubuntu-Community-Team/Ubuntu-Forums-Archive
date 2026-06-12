---
title: "AWN Trunk Failed To Install Unment Dependancies"
date: 2011-03-12
forum: General Help
---

### Post by techunit on 2011-03-12
While trying to install AWN Trunk today I ran in to this error

```
tobias@tobias-Studio-1737:~$ sudo apt-get install avant-window-navigator-trunk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 avant-window-navigator-trunk : Depends: avant-window-navigator-data-trunk (>= 0.4.1~bzr822+201102140003~maverick1) but it is not going to be installed
E: Broken packages
```

What I have tryed.

Sudo apt-get install -f  
checked synaptic for broken packages: NO
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg -a --configure
sudo apt-get -V install avant-window-navagator-trunk

Nothing with any of these.


Any ideas what the problem could be. Tested on two fresh installs still no problem.

Talked to the AWN team and they suggested a trasitory from problem. I have been watching the build times for the Maverick release and it has just been built. If this isn't going to help solve the problem Could you take a look.

Thanks a lot, sincerely,

Tobias

---

### Post by techunit on 2011-03-12
I love how all my problems are all to complicated for the anyone to help solve. Disgruntled Bump.

---

### Post by arsham on 2011-03-12
I'm having the same problem ( just about now )
Seems that the proper dependencies are not in the repository yet, you need to wait..

---

### Post by Frogs Hair on 2011-03-12
I have one Awn package that failed to install as well , the last time this happened I just waited because the the update was not complete.   Just leave it in the update manager and try later or it will all end in tears or someone will loose an eye.  :P

---

### Post by Frogs Hair on 2011-03-12
I just received the balance  of the Awn packages and the update is complete.

---

### Post by techunit on 2011-03-12
Yeah I fixed my problem and my desktop is all in fading order.

---

### Post by techunit on 2011-03-12
It turned out to be build errors with the amd64 build of AWN trunk I chatted with the team via IRC and they very kindly fixed the problem in a few hours.

---

### Post by Frogs Hair on 2011-03-12
I received the updates within a half an hour of posting here you must have contacted them much earlier  Thank you .

---

### Post by techunit on 2011-03-12
I had the problem around 8am Central Standard Time.

---

