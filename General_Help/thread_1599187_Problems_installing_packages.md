---
title: "Problems installing packages"
date: 2010-10-17
forum: General Help
---

### Post by tustus on 2010-10-17
Hey all, I'm trying to install Insight Toolkit and Visual toolkit. I was able to apt-get most of the packages that I need, but I am stuck on VTK.  From my understanding I am unable to get the packages needed for some C++ booster libraries. 

I tried to apt-get libboost-all-dev, and I keep getting the same result as with libvtk, but with a different dependency issue. I'm stuck, and any help would be greatly appreciated.

daniel@BaseStation:~$ sudo apt-get install libvtk5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libvtk5-dev: Depends: libboost-all-dev but it is not going to be installed
E: Broken packages

---

