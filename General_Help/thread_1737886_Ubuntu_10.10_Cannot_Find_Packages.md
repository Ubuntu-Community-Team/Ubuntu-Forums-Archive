---
title: "Ubuntu 10.10 Cannot Find Packages"
date: 2011-04-24
forum: General Help
---

### Post by Baileyn1 on 2011-04-24
Hello, I just recently installed Ubuntu on an older computer of mine to boost it's performance, and have some fun with the open source OS. Upon installation, I discovered Ubuntu could not find my wireless card and tried to install NdisWrapper to remedy this problem. After this failed, (and I'm still working with it) I tried to at least install ARandR to configure my screen resolution. Again, Ubuntu's terminal failed to find the packages I needed for install. I am attempting this after a fresh install, and was under the impression that these packages came preloaded with the install. Below is the code it returned. Any help would be greatly appreciated. Thank you for your time. 
Code: 
$ sudo apt-get install ndiswrapper
Reading package lists... Done
Reading state information... Done
E: Unable to locate package ndiswrapper

$ sudo apt-get install ARandR
Reading package lists... Done
Reading state information... Done
E: Unable to locate package ARandR

---

### Post by andrewthomas on 2011-04-24
Because that is not the name of the package.

ndiswrapper-utils-1.9

[http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9](http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9)

arandr

[http://packages.ubuntu.com/maverick/arandr](http://packages.ubuntu.com/maverick/arandr)

---

### Post by Baileyn1 on 2011-05-06
I apologize for the misleading code. I mixed the codes I was using (the one for installing, and the one for verifying that the program was running). Even with the correct application name (ndiswrapper-utils-1.9) the terminal still returns the same code, with the exception of the "utils-1.9" added to the end. And that still doesn't address the lack of the arandr package.

---

