---
title: "Kernel 2.6.35.7 - CPU stalling problem - if system  is unattended/idle"
date: 2011-01-07
forum: General Help
---

### Post by gpraveenya on 2011-01-07
Hi, 

I am facing a peculiar problem with the default kernel shipped with ubuntu netbook remix 10.10(running linux-kernel 2.6.35.7). I installed ubuntu netbook remix on my ATOM processor based system from latest iso downloaded from ubuntu site.

If u leave the computer unattended  the processing stops as it is, may be cpu is halting or by some other reason. For example while booting, the boot process proceeds only if you are moving mouse or pressing any keys on keyboard. I mean If you are not entering any mouse/keyboard events the boot process halts. Similar behaviour can be observed during entire functioning of OS like copying a file or shutdown. It seems like cpu stall on system idle.  


I reproduced the same problem on one of my atom processor where redhat was running fine. I downloaded [http://packages.ubuntu.com/maverick/linux-source-2.6.35](http://packages.ubuntu.com/maverick/linux-source-2.6.35) and used the kernel's .config of ubuntu_netbook_remix installed on another atom processor based machine and compiled. This new kernel also showing the same behaviour.  Please check the link [http://paste.uni.cc/21164](http://paste.uni.cc/21164) for the kernel's .config file that I used.


Can sombody suggest how to avoid this problem.



Thanks

praveen

---

