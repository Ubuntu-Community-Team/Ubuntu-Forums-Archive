---
title: "ATI Proprietary Drivers (Catalyst 10.9)"
date: 2010-09-18
forum: General Help
---

### Post by Acidphase on 2010-09-18
Okay allot of people been having problems with this, or at least I was and saw a few others.

Heres what I did when I first downloaded the newest drivers then I made a custom directory "catalyst" and put the ati-driver-installer-10-9-x86.x86_64.run in it.

Then I ran:
sudo sh ./ati-driver-installer-10-9-x86.x86_64.run --buildpkg Ubuntu/lucid

It built the packages no problem but when I went to install them I was getting a dependency issue when I ran:

sudo dpkg -i *.deb

[http://paste.ubuntu.com/496062/](http://paste.ubuntu.com/496062/)

I got those errors.


(After rebooting and running synaptic and doing a search on the fglrx I removed it manually then did the following)
 
Very simple fix don't build Dist. specific packages just run:

sh ./ati-driver-installer-10-9-x86.x86_64.run

Follow the GUI install again don't have to generate the custom packages just select continue and use auto install.

When it's all done DO NOT use the aticonfig --initial as it says to just reboot. 
All should be fine.

--
I'm using:

uname -a

 2.6.35-14-generic #20~lucid2-Ubuntu
-
fglrxingo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series
OpenGL version string: 1.4 (4.0.10188 Compatibility Profile Context)
----

Hope this helps someone :)

---

