---
title: "3 upates available"
date: 2011-08-11
forum: General Help
---

### Post by conradin on 2011-08-11
Hi All, 
I am dealing with a kernel bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699)

of which the solution is evidently to update the kernel.
when I run ```
sudo apt-get upgrade
```
I get a message saying that 3 kernel updates exist but are not being upgraded. "kept back" I think this is a throw back from some configuration of the Update manager GUI. Since I cannot log into a gui to set the computer to update the kernel, I need some way to tell ubuntu to upgrade the kernel fro the command line. Can some one point me in the right direction?

I am using 64-bit Ubuntu, version 10.10
the 3 kernel updates are:
linux-generic
linux-headers-generic
linux-image-generic

---

### Post by dino99 on 2011-08-11
first run: 
clean/autoclean/autoremove to clean the system
then: sudo dpkg --configure -a

better to use one of the latest kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

download into an empty folder: 
linux-headers...all.deb,
linux-headers...amd64.deb 
and linux-image...amd64.deb

then cd to that folder and: sudo dpkg -i *

and finally:
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade

---

### Post by conradin on 2011-08-12
Should I get the AMD64 kernel? This is a 64bit (i7) Intel CPU.

---

### Post by wojox on 2011-08-12
> **conradin said:**
> Should I get the AMD64 kernel? This is a 64bit (i7) Intel CPU.

I had that same problem. Try waiting a day or two. That fixed it for me.

---

### Post by mcduck on 2011-08-12
> **conradin said:**
> Should I get the AMD64 kernel? This is a 64bit (i7) Intel CPU.

the 64-bit architecture used on PCs  is called AMD64, regardless of which company actually built your CPU. AMD developed the architecture, so they also got the chance to name it. ;)

Anyway, like wojox suggested, that kind of problems tend to go away on their own if you wait a while and then try updating again. Sometimes you just happen to try to update the time when new packages are being loaded into repositories, so everything required might not be available at the very moment.

---

### Post by gmargo on 2011-08-12
> ```

sudo apt-get upgrade

```Try using the "dist-upgrade" command on **apt-get( 8 )** instead:
```

sudo apt-get update
sudo apt-get dist-upgrade

```Alternatively use "full-upgrade" on **aptitude( 8 )**:
```

sudo aptitude update
sudo aptitude full-upgrade

```

---

