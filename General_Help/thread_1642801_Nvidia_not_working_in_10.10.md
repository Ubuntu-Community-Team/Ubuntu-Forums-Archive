---
title: "Nvidia not working in 10.10"
date: 2010-12-10
forum: General Help
---

### Post by Pollyanna1 on 2010-12-10
I do not know what happened, but the story was:
 
I put fresh installation for ubuntu 10.10 and when I try to install the driver for nvidia was not working as in 10.04. I put fresh installation for ubuntu 10.04 after that, I install Nvidia GeForce4 MX 420 easily through appearance, actually was installed by itself. Then, When I upgrade to 10.10 the system gave me warning about upgrading compize application (and other warnings as well but I do not remember them now), I just choose continue with the upgrade. 
After I finished upgrading, I restart the computer and I got the command line.  I was not be able to enter the X system ( mouse interface) or you can say I do not know how to exist from command line (I did restart the computer many times, but does not help), then I just install ubuntu 10.10 again, but the nvidia did not install when I chose appearance as what I did in ubuntu 10.04..
 
Is that normal when I use upgrade like that? or ubuntu 10.10 does not support Nvidia GeForce4 MX 420 any more? 
 
I hope the story is clear. if need more clarification I will do so.
 
Thanks,

---

### Post by GJLenon on 2010-12-11
I am having a very similar issue.

I've tried multiple things to fix my problem, everything from using "rm" on the xorg.conf file and doing a reboot (this gets the GUI back up, but that's about it) to trying to open an older kernal.  

[s]I could be wrong, this is entirely supposition, but I am thinking that the nvidia drivers are having issues keeping the nomodeset in the kernal.[/s]  Nevermind, trying to load the live CD in nomodeset accomplished nothing.

I will tell you this, if you are indeed having the same issue I am, inserting the live CD will not work either.  :)  I'll post a reply as soon as I figure out a solution, hopefully it'll fix both our issues.

-Greg

---

### Post by dawghed on 2010-12-21
After spending too much time trying to resolve the Nvidia 96 incompatibility with 10.10 I have come up with a solution... Revert back to 10.4 until Ubuntu and Nvidia resolve the problem.

---

### Post by Malta paul on 2010-12-21
Check out #4 in this link:
[http://ubuntuforums.org/showthread.php?t=1609725](http://ubuntuforums.org/showthread.php?t=1609725)
This should work for you ;)

---

### Post by FahadMKS on 2010-12-21
Please click on the link [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and then give the information needed there and try to install the Nvidia Driver manually and install it and then check if you get the issue resolved.

---

