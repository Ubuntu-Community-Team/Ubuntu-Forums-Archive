---
title: "libgimp-dev dependencies cannot be resolved"
date: 2011-02-16
forum: General Help
---

### Post by Quixotico on 2011-02-16
I have GIMP 2.6 installed on Ubuntu 10.10 and am trying to install a script.

[http://registry.gimp.org/node/20069](http://registry.gimp.org/node/20069)

The script is only offered as .c and must be compiled.  In a terminal, I get this:
> gimptool-2.0 --install smooth-path.c
The program 'gimptool-2.0' is currently not installed.  You can install it by typing:
sudo apt-get install libgimp2.0-dev

So I try that:
> sudo apt-get install libgimp2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgimp2.0-dev : Depends: libgimp2.0 (= 2.6.10-1ubuntu3.1) but 2.6.11-1~getdeb1~maverick is to be installed
E: Broken packages


Going into the Software Center, I locate libgimp-dev and attempt to install it through there.
> **Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details
libgimp2.0-dev

Any help is appreciated.

---

