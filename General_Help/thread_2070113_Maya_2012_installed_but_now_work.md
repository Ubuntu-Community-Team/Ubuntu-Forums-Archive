---
title: "Maya 2012 installed but now work"
date: 2012-10-12
forum: General Help
---

### Post by hamedasl on 2012-10-12
hi to every one...

i'm new to ubuntu and want to use maya on it...

i'm googeling and red some Thread about installing maya and whit this code i install therpm package:

```
sudo rpm -ivh --nodeps adlmapps4-4.0.35-0.x86_64.rpm adlmflexnetclient-4.0.35-0.x86_64.rpm adlmflexnetserver-4.0.35-0.x86_64.rpm autodesk.backburner.monitor-2012.0.0-424.i386.rpm backburner.sw.base-2012-1561.i386.rpm backburner_webmonitor.sw.base-2012-1561.i386.rpm Composite_2012-2012.0-2502.x86_64.rpm dmmPluginForMaya2012.x86_64.rpm MatchMover2012_0_64-2012.0-622.x86_64.rpm Maya2012_0_64-2012.0-203.x86_64.rpm
```

finaly recive that:

```

package backburner.sw.base-2012-1561.i386 is already installed
	package backburner_webmonitor.sw.base-2012-1561.i386 is already installed
	package Maya2012_0_64-2012.0-203.x86_64 is already installed
	package MatchMover2012_0_64-2012.0-622.x86_64 is already installed
	package dmmPluginForMaya2012x64-1.1.9-4.x86_64 is already installed
	package Composite_2012-2012.0-2502.x86_64 is already installed
	package autodesk.backburner.monitor-2012.0.0-424.i386 is already installed
	package adlmflexnetserver-4.0.35-0.x86_64 is already installed
	package adlmflexnetclient-4.0.35-0.x86_64 is already installed
	package adlmapps4-4.0.35-0.x86_64 is already installed

```

the icon of the program add to my dash but when i click on it it dont work...i also try Bin folder of maya  and run maya file manualy but nothing happend ...

plz help me to run this great program ...


tanx :)

---

### Post by shreepads on 2012-10-12
Open terminal and run from there.. It should show some error messages, paste them here...

---

### Post by hamedasl on 2012-10-12
tanx for your Quick answer shreepads :)

is this the error when run it from terminal:

```
/usr/autodesk/maya2012-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

```

---

### Post by Mark Phelps on 2012-10-12
Ubuntu uses .deb files for installations, not .rpm files.  While the latter CAN work, I've had problems where the libraries required in .rpm installations have different names than those installed in Ubuntu.

It's best to install from .deb packages.

In this case, the error message indicates you're missing a library -- which you'll have to track down and install.

And ... don't be surprised if then, you get another message indicating another library is missing.

---

### Post by hamedasl on 2012-10-13
tank you but where can i find the .deb package for maya?

in my search all of maya installation IS FROM .RPM files...

---

### Post by hamedasl on 2012-10-17
nothing?

---

### Post by ubh on 2012-10-17
> **hamedasl said:**
> tanx for your Quick answer shreepads :)

is this the error when run it from terminal:

```
/usr/autodesk/maya2012-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

```[http://ubuntuforums.org/showthread.php?t=1885911](http://ubuntuforums.org/showthread.php?t=1885911)
[http://askubuntu.com/questions/44132/how-do-i-install-libtiff-so-3](http://askubuntu.com/questions/44132/how-do-i-install-libtiff-so-3)

---

### Post by vkadal on 2012-10-18
You can use blender instead of Maya which is completely free

---

