---
title: "Can't install virtualbox-3.2 anymore?"
date: 2011-05-23
forum: General Help
---

### Post by Xavier Oddmon on 2011-05-23
I write apps for webOS, and need to use the palm emulator. The emulator runs on virtualbox-3.0 to virtualbox-3.2 only (no support for virtualbox 4). 

After adding the virtualbox source, I still cannot install virtualbox-3.2, and am instead given the error:
> 
Package virtualbox-3.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'virtualbox-3.2' has no installation candidate


I tried downloading and installing the virtualbox-3.2 package from the web site, but it does not run. The contents of /var/log/vbox-install.log are as follows:
> 
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  3.2.12

------------------------------
Deleting module version: 3.2.12
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/3.2.12/source ->
                 /usr/src/vboxhost-3.2.12

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-8-generic -C /lib/modules/2.6.38-8-generic/build M=/var/lib/dkms/vboxhost/3.2.12/build....(bad exit status: 2)
0
0
Failed to install using DKMS, attempting to install without
Makefile:170: *** Error: /usr/src/linux (version 2.6.38.2) does not match the current kernel (version 2.6.38-8-generic).  Stop.


Is there some way that I can get this package installed?

---

### Post by linuxinstalledfromhdd on 2011-05-23
Try installing the latest version..

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

The PPA for virtualbox 4 is near the bottom of the walkthrough.

---

### Post by vake on 2011-05-26
the latest palm emulator won't work with virtualbox 4.0

---

### Post by vake on 2011-05-26
well I can start palm emulator from virtualbox 4.0. Typing "palm-emulator" from the command line doesn't work anymore.

---

### Post by Xavier Oddmon on 2011-05-26
Thanks, but the palm emulator doesn't run under virtualbox 4. In addition, I don't have any machines when I run virtualbox manually, so I don't know how to start it other than with "palm-emulator"

---

### Post by Toz on 2011-05-26
> **Xavier Oddmon said:**
> Makefile:170: *** Error: /usr/src/linux (version 2.6.38.2) does not match the current kernel (version 2.6.38-8-generic). Stop. Looks like your kernel headers don't match your current kernel. What do the following commands return:
```
uname -r

apt-cache policy linux-image-$(uname -r)

apt-cache policy linux-headers-$(uname -r)
```

---

### Post by Xavier Oddmon on 2011-05-27
I've got this:
```

chris@chris-EX700:~$ uname -r
2.6.38-8-generic
chris@chris-EX700:~$ apt-cache policy linux-image-$(uname -r)
linux-image-2.6.38-8-generic:
  Installed: 2.6.38-8.42
  Candidate: 2.6.38-8.42
  Version table:
 *** 2.6.38-8.42 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main amd64 Packages
        100 /var/lib/dpkg/status
chris@chris-EX700:~$ apt-cache policy linux-headers-$(uname -r)
linux-headers-2.6.38-8-generic:
  Installed: 2.6.38-8.42
  Candidate: 2.6.38-8.42
  Version table:
 *** 2.6.38-8.42 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Toz on 2011-05-27
```
sudo ln -s /usr/src/linux-headers-`uname -r`/include/generated/autoconf.h /usr/src/linux-headers-`uname -r`/include/linux/autoconf.h
```

and try again. 

Out of curiosity, where did you get the 3.2 Virtualbox package for Natty? I can't find it anywhere on the virtualbox site.

---

### Post by wildmanne39 on 2011-05-27
> **Xavier Oddmon said:**
> I write apps for webOS, and need to use the palm emulator. The emulator runs on virtualbox-3.0 to virtualbox-3.2 only (no support for virtualbox 4). 

After adding the virtualbox source, I still cannot install virtualbox-3.2, and am instead given the error:
 

I tried downloading and installing the virtualbox-3.2 package from the web site, but it does not run. The contents of /var/log/vbox-install.log are as follows:


Is there some way that I can get this package installed?

Hi, I went to virtualbox.org and they have the 3.2 for older builds the newest is ubuntu 10.10, if you follow there manual you should be able to install it and make it work, it is neccessary to install dkms package first then install virtualbox and it should build against the kernel you have installed, that is if being that old it will let you.

---

