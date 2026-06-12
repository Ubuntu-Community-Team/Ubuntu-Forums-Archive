---
title: "problem to install and run 32bits application on Ubuntu 11.04 64bits"
date: 2011-10-03
forum: General Help
---

### Post by rvboutin on 2011-10-03
Hi,
I am running into a problem when I try to install or run 32bits application on Ubuntu 11.04 64bits.
I have searched extensively the net for solution but none has worked so far, or they are so complicated that I don't even know where to start...
So, for example I cannot install Wine or flash, or run some small tools that are crucial for my work.
Every time the problem is down to the ia32-libs being missing, when I try to install it I am running into dependencies problem that I cannot solve.
**NB: I have tried many solution found on the web using Synaptic and apt-get: they did not work unfortunately.**
The error message is:
```
The following packages have unmet dependencies.
 ia32-libs : Depends: lib32v4l-0 but it is not going to be installed
E: Broken packages
```
If I try to install lib32v4l-0  I got this one:
```
The following packages have unmet dependencies.
 lib32v4l-0 : Depends: libv4l-0 (= 0.8.3-2~ppa1) but 0.8.5-3u1~ppa1 is to be installed
E: Broken packages
```
I have installed libv4l-0 (= 0.8.3-2~ppa1), but as the 0.8.5-3u1~ppa1 is already installed, I think that it does not install correctly and therefore does not solve the problem.
I have tried the repair broken package option in Synaptic, but it does not want to proceed...
So, I am kind of stuck here... it seems to me that it is a maze of dependencies that I'll never solved ](*,)
If someone could help that would be great \\:D/
but please do not tell me to just try to install these libraries via a console or Synaptic ```
apt-get install libv4l-0
``` or similar things =;, as I have already tried them and they do not work.
PS: I have also tried to force the install:
```
apt-get install -f libv4l-0
```, and it did nor work, but maybe I place the -f at the wrong place?
Thank you in advance for your help!
Cheers,
Rv

---

### Post by dino99 on 2011-10-03
from oneiric repo:

ia32-libs-multiarch
This package depends on i386 versions of packages that were removed from
ia32-libs and transitioned to multi-arch.  This allows applications using
ia32-libs in previous Ubuntu releases to continue functioning without missing
libraries.

for info:
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by rvboutin on 2011-10-03
> **dino99 said:**
> from oneiric repo:

ia32-libs-multiarch
This package depends on i386 versions of packages that were removed from
ia32-libs and transitioned to multi-arch.  This allows applications using
ia32-libs in previous Ubuntu releases to continue functioning without missing
libraries.

for info:
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

Thanks Dino99, I agree with what is said on the link you said, but I had no choice than to move to 64bits as the guys who develop software and with whom I collaborating have only the 64bits version (for now?) as they require huge amount of RAM to work with.
Thanks for your reply anyway, how do I add the oneiric repo to get thess files?? would synaptic do? Or shall just upgrade to Oneiric Beta now?
Cheers,):P
Rv

---

