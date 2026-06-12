---
title: "nvidia-legacy troubles: libdrm.so.1 missing"
date: 2006-06-02
forum: General Help
---

### Post by schilcha on 2006-06-02
I just upgraded my acer travelmate (geforce2 go) from breezy to dapper, which worked fine.

I had some troubles with x11, since I had installed a newer nvidia driver (81?? I think) under breezy. This installation was naturally broken during the upgrade. Since I no longer need a newer driver (I tried it when messing around with twinview), I wanted to go back to the nvidia-glx-legacy package. This works to some extent: nvidia-server starts and I can work with it.

But my problem is:
> 
glxheads: error while loading shared libraries: libdrm.so.1: cannot open shared object file: No such file or directory

This is consequently the same for all other glx* tools. 
It seems, there's no OpenGL-acceleration :(

So, I tried installing it:
> 
$ sudo apt-get install libdrm1
Password:
Reading package lists... Done
Building dependency tree... Done
Package libdrm1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdrm1 has no installation candidate

libdrm1 obviously is no longer in the repos.

Where is it?

Any help is greatly appreciated!

---

### Post by schilcha on 2006-06-05
It took me some time to figure out... therefore, I'll answer myself... maybe it'll help someone.

So, here's again my situation (actually all this started quite some time ago):
1) Breezy installation with nvidia-glx-legacy package installed
2) For some reason, I installed the latest nvidia driver according to some howto here (without removing nvidia-glx-legacy first)
3) Upgrade to dapper
4) Removal of the latest nvidia-driver using the deinstallation-script from nvidia

Here are the symptoms:
1) nvidia-driver work without accelerated opengl
2) glxgears didn't start, giving some error like "cannot find library libdrm.1.so

Here's what helped me:
1) Deinstall nvidia-glx-legacy. There were some dpkg-divertion error -- search this forum for the error-message and you'll find a thread that describes how to deal with the divertion-error (a very simple solution: just rename the offending files). 
2) Reinstall libdrm.so.2 by downloading the .deb-file and installing it using dpkg -i (for some reason reinstallation in synaptic didn't suffice)
3) Anew installation of nvidia-glx-legacy.

Good luck to everyone with (and of course without) that problem!

---

