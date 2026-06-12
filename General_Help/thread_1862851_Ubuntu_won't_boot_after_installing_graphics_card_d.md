---
title: "Ubuntu won't boot after installing graphics card driver"
date: 2011-10-17
forum: General Help
---

### Post by djriley on 2011-10-17
I installed the latest version of Ubuntu on my new computer a few weeks ago in dual-boot mode with Windows 7. Everything was working fine until I installed the driver for my Sapphire Radeon HD 6870 and now I can't even boot Ubuntu at all. If I try to boot into Ubuntu I just get this screen: [http://imgur.com/idn0A](http://imgur.com/idn0A)

Someone please help. :confused:

---

### Post by kaldor on 2011-10-17
Did you use the driver in Jockey ("Additional Hardware" app) or did you get it from AMD's website?


Edit: [_This here_]("http://askubuntu.com/questions/67065/system-doesnt-boot-after-amd-11-9-driver-install") might help.

---

### Post by djriley on 2011-10-18
> **kaldor said:**
> Did you use the driver in Jockey ("Additional Hardware" app) or did you get it from AMD's website?


Edit: [_This here_]("http://askubuntu.com/questions/67065/system-doesnt-boot-after-amd-11-9-driver-install") might help.

I followed that guide and can now boot Ubuntu, but now I have the same issue I did before I installed the graphics card drivers where the whole screen is flickering purple and white. I know the OS is loading because I can hear that bongo sound when the login prompt pops up. Is there a way to install the drivers without it messing up the whole system?

---

### Post by djriley on 2011-10-19
Can anyone help?

---

### Post by Mark Phelps on 2011-10-19
If you installed 11.10 "a few weeks ago", you installed a Beta version, so you did right NOT installing the restricted drivers.

Unfortunately, once again, a new Ubuntu release comes with AMD drivers problems -- and until AMD gets their act together and FINALLY puts out a new version of their Linux drivers that work, these problems will continue.

Sorry, but there is no immediate solution.

---

### Post by searchfgold6789 on 2011-10-19
AMD has yet to make their drivers work with the new kernel, actually. Nvidia has the same problem, except all you need to do with the Nvidia drivers is reinstall them (irrelevant).
Try installing a different kernel (press Ctrl + Alt + F1 and log in) using the command line and then reinstall the graphics drivers.

---

### Post by djriley on 2011-10-19
Thanks heaps guys. I guess I'll just use Windows until the drivers come out.

---

### Post by djriley on 2011-10-25
Okay so I tried booing ubuntu today and it worked for some reason. I've been trying to boot it many times over the last week or so and nothing, but it worked every time I tried it today. Weird.:-?

---

