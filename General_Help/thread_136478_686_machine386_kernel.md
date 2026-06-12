---
title: "686 machine/386 kernel:"
date: 2006-02-26
forum: General Help
---

### Post by klepto on 2006-02-26
Is it worth installing a new kernel since the default kernel on install is a 386 and the machine is a 686? Will there be any noticeable difference?

Linux ANTIPATHY 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

---

### Post by bikeboy on 2006-02-26
I run the 686 kernel on my PIII 900, I honestly haven't noticed the difference. Maybe there is only a small one or maybe I don't run enough of the things that have optimisations.

Having said that, this is probably the guide you want to look at

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by der_joachim on 2006-02-26
It's most definitely worth the trouble to install the right kernel image. Ever since I switched to the K7 image (I have an Athlon XP), the average temperature of my proc's temperature is significantly lower.

---

### Post by Jucato on 2006-02-26
not only that, the kernel version that is installed is 2.6.12-**9**, and the latest available (from the repositories) is 2.6.12-**10**. I'm not sure, but I think that the upgrade might fix some kernel bugs/issues as well.

---

### Post by klepto on 2006-02-26
Wow.. that was a bad idea... I tried to install the module ndiswrapper in the new K7 kernel
and got the dreaded "unknown symbols" bug which has to do with the kernel itself not
having something set. Although I did notice that applications loaded like a couple secs faster.

C'est la vie..[-(

---

### Post by az on 2006-02-26
[QUOTE=klepto]Wow.. that was a bad idea... I tried to install the module ndiswrapper in the new K7 kernel
and got the dreaded "unknown symbols" bug which has to do with the kernel itself not
.[-([/QUOTE]


Yes, you should install the proper kernel, it is better.  

What exactly did you install regarding ndiswrapper?

To run ndiswrapper, just use the version that comes with ubuntu.  The module is already there.  You just have to install the ndiswrapper-utils package to use it.

If you own one of the five-or-so devices that requires that you use the latest ndiswrapper, install the linux-headers package for your kernel (386, 686, k7 whatever) and build it with that.

---

### Post by klepto on 2006-02-26
Yup,

I downloaded the new k7 kernel as well as all the headers and everything
told ndiswrapper where the headers was and got that nasty "unknown symbol" 
error. Last time I checked ndiswrappers on the repos was broken. I compiled
the ndiswrappers from src.

---

### Post by Rizado on 2006-02-26
If you want a faster kernel, compile the latest from kernel.org and apply the -ck patches. Do this right and you'll notice a big difference. (2.6.12 are really old)
Just run lsmod in a terminal and you'll see all the unnecessary modules that's loaded. In my case there were ethernet cards and sound cards I didn't even have.

---

### Post by az on 2006-02-26
[QUOTE=klepto]I downloaded the new k7 kernel as well as all the headers and everything
told ndiswrapper where the headers was and got that nasty "unknown symbol" 
error. Last time I checked ndiswrappers on the repos was broken. I compiled
the ndiswrappers from src.[/QUOTE]

If you are running a 686 processor, the k7 headers (and linux-image) are wrong for you.

As for ndiswrapper being broken, try using the most recent .inf file for your drivers. The one that came with your card is probably the problem.  There are very few cards that require you recompile ndiswrapper to a newer version.

---

