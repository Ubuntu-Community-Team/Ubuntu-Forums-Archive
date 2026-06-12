---
title: "VirtualBox error on Xfce"
date: 2010-04-04
forum: General Help
---

### Post by luftadler on 2010-04-04
Hi,

I have a problem with Virtual Box, when I try to start installation of XP it gives me this error:

```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) 
is either not loaded or there is a permission problem with /dev/vboxdrv. 
Please reinstall the kernel module by executing

'**/etc/init.d/vboxdrv setup**'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. 
This package keeps track of Linux kernel changes and recompiles the vboxdrv 
kernel module if necessary.
```I've try this : **sudo /etc/init.d/vboxdrv setup**
```
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.
```... but without success, the problem is the same, and the DKMS package is installed on the system

Is this a bug? Anyone has this problem? 

Any ideas how to resolve this?




Thanks!!!
Cristian

---

### Post by luftadler on 2010-04-04
also I've try this: 

```
sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup
```

from this post [http://ubuntuforums.org/showthread.php?t=1163811](http://ubuntuforums.org/showthread.php?t=1163811)

but is not working...

---

### Post by luftadler on 2010-04-04
problem solved

i found here the solution here
[http://ubuntuforums.org/showthread.php?t=1313989](http://ubuntuforums.org/showthread.php?t=1313989)
```

sudo vim /etc/modules
```and add this line: [B]vboxdrv
[/B]
save and rebootNow works[B]!
:D
[/B]

---

