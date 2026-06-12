---
title: "Help installing virtual box..!"
date: 2010-05-03
forum: General Help
---

### Post by karthick87 on 2010-05-03
I have installed virtual box,but it tells that [COLOR=Red]"starting virtual box kernel module was failed" [COLOR=Black]wat it mean..?

[/COLOR][/COLOR]```

karthick@Learners-desktop:~$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting virtualbox-ose instead of virtualbox
The following extra packages will be installed:
  dkms fakeroot virtualbox-ose virtualbox-ose-source
Suggested packages:
  bridge-utils
The following NEW packages will be installed:
  dkms fakeroot virtualbox-ose virtualbox-ose-source
0 upgraded, 4 newly installed, 0 to remove and 9 not upgraded.
Need to get 9586kB of archives.
After this operation, 36.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  virtualbox-ose dkms fakeroot virtualbox-ose-source
Install these packages without verification [y/N]? y
Get:1 http://archive.ubuntu.com jaunty/universe virtualbox-ose 2.1.4-dfsg-1ubuntu3 [8783kB]
Get:2 http://archive.ubuntu.com jaunty/main dkms 2.0.21.1-0ubuntu3 [57.6kB]    
Get:3 http://archive.ubuntu.com jaunty/main fakeroot 1.12.1ubuntu1 [115kB]     
Get:4 http://archive.ubuntu.com jaunty/universe virtualbox-ose-source 2.1.4-dfsg-1ubuntu3 [630kB]
Fetched 3921kB in 1min 13s (53.0kB/s)                                          
Selecting previously deselected package virtualbox-ose.
(Reading database ... 110885 files and directories currently installed.)
Unpacking virtualbox-ose (from .../virtualbox-ose_2.1.4-dfsg-1ubuntu3_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.0.21.1-0ubuntu3_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.1ubuntu1_i386.deb) ...
Selecting previously deselected package virtualbox-ose-source.
Unpacking virtualbox-ose-source (from .../virtualbox-ose-source_2.1.4-dfsg-1ubuntu3_all.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up virtualbox-ose (2.1.4-dfsg-1ubuntu3) ...
[B] * Starting VirtualBox kernel module...                                  [[COLOR=Red]fail[/COLOR]] 
[/B]
Setting up dkms (2.0.21.1-0ubuntu3) ...
 * Running DKMS auto installation service for kernel 2.6.28-11-generic   [ OK ] 

Setting up fakeroot (1.12.1ubuntu1) ...

Setting up virtualbox-ose-source (2.1.4-dfsg-1ubuntu3) ...
 * Reloading kernel event manager...                                     [ OK ] 
Adding modules to DKMS build system
Doing initial module builds
Installing initial modules
Done.
 * Stopping VirtualBox kernel module...                                  [ OK ] 
 * Starting VirtualBox kernel module...                                  [ OK ] 

Processing triggers for menu ...


```

---

### Post by snowpine on 2010-05-03
Make sure you add yourself to the 'vboxusers' group... that is likely the problem. :)

---

### Post by karthick87 on 2010-05-03
> **snowpine said:**
> Make sure you add yourself to the 'vboxusers' group... that is likely the problem. :)


How to do it..?

---

### Post by snowpine on 2010-05-03
System->Administration->Users and Groups

First things first, though... I see later on in your terminal output that the module was successfully loaded, so does VirtualBox work? If it works OK, you are done. :)

---

### Post by karthick87 on 2010-05-03
> **snowpine said:**
> System->Administration->Users and Groups

First things first, though... I see later on in your terminal output that the module was successfully loaded, so does VirtualBox work? If it works OK, you are done. :)


Yes its working...!

---

