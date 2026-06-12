---
title: "For those of you seeing corruption with google earth and the X.org radeon driver..."
date: 2006-06-21
forum: General Help
---

### Post by siriusnova on 2006-06-21
add these two repositories to your sources.list (it's from the AIGLX howto thread)

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

and do an update (WARNING IM NOT RESPONSIBLE IF YOUR SYSTEM BREAKS)

the 2 repositories contain updated radeon drivers and fixes for X.org, opengl etc.. that allowed me to run Google Earth and other games without problems or texture corruption :D

you should probably also do

sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r` 

to install the latest dri modules for your system.
i didn't do the 'uname-r' i just added them manually through synaptic, do that if you have troubles installing the packagee through aptitude


If you have problems with your restricted modules not loading (atheros cards etc..)

then do -> sudo /sbin/ldm-manager to rebuild your modules.dep (then reboot)

---

