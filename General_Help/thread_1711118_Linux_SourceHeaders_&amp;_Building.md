---
title: "Linux Source/Headers &amp; Building"
date: 2011-03-20
forum: General Help
---

### Post by jeffrich4 on 2011-03-20
I'm a bit confused about the linux source. When a program asks for me to point to the linux source when compiling/building, ie. change the path in a Makefile, should I be pointing it to a source that has been built? I have downloaded the linux source from the Synaptic package manager, but I'm not sure if I need to build it or not, or if I'm even understanding it right. It seems like I'm already running a linux source that has been built, so I'm not sure why I would need to build it again. The example I'm referring to is with relates to Logitech web cams and the tutorial @ [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

It wants headers and the linux source to be able to build, but everytime I point it to source directory, it says that it has not been configured properly. And since I'm running the latest kernel it requires the source to be built, as opposed to just using the headers.

Any help would be much appreciated :)

---

### Post by bleedingsamurai on 2011-03-20
well, if you need headers try running this
```
sudo apt-get install linux-headers-$(uname -r)
```
after that Make *should* take care of the rest. it doesn't look like you need to entirely rebuild your kernel, you are just building kernel modules

---

