---
title: "Can't Install FGLRX Driver (Gone from Hardware Drivers and Manual Install Failed)"
date: 2010-09-28
forum: General Help
---

### Post by boaty on 2010-09-28
Hey everyone,

Because of a bug somewhere in vinagre or compiz (or who knows where), I disabled my graphics driver to attempt to get my remote desktop screen to refresh.  Well it didn't work, and know I can't install the proprietary FGLRX driver again.  As the title states, it's gone from the Hardware Drivers screen and doing a manual install failed.

I'm running Ubuntu 10.04 with the 2.6.32-25-generic kernel.
I'm using an ATI 5830

I followed this [HowTo]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to get my driver manually installed.  It failed when I got to the point of
```
sudo dpkg -i *.deb
```

I got this error:
```


sudo dpkg -i *.deb
Selecting previously deselected package fglrx.
(Reading database ... 246090 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.771-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.771-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.771-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-modaliases.
Unpacking fglrx-modaliases (from fglrx-modaliases_8.771-0ubuntu1_amd64.deb) ...
Setting up fglrx (2:8.771-0ubuntu1) ...
Loading new fglrx-8.771 DKMS files...
Building only for 2.6.32-25-generic
Building for architecture x86_64
Building initial module for 2.6.32-25-generic

Error! Bad return status for module build on kernel: 2.6.32-25-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.771-0ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev

```

I read through this, and it says fglrx hasn't been configured.  The fact that the HowTo was for Karmic may have been the problem, but I can't find any other tutorials (currently searching).

If anybody could help me figure out why the fglrx driver disappeared from Hardware Drivers or how to install it manually, I would be extraordinarily grateful.

Thanks in advance

EDIT:
So first I uninstalled the fglrx packages created by the above HowTo.  Then I found [this post]("http://ubuntuforums.org/showthread.php?t=1439583").  I did
```

sudo apt-get install fglrx

```
which seemed to installed both fglrx and fglrx-amdcccle (along with other stuff probably...).
Then I went to Hardware Drivers and found the driver was there!  I'm about to restart to see if it will now work.

EDIT 2:
So I restarted, and it's working.  Just one thing though...I see people say it's important to run ```
sudo aticonfig --initial
```, yet when I run that code it says "aticonfig: No supported adapters detected".  Should I worry about that?

---

