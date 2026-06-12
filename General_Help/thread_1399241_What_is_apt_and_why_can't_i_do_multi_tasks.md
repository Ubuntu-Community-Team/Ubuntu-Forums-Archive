---
title: "What is apt?? and why can't i do multi tasks?"
date: 2010-02-05
forum: General Help
---

### Post by TommyDean on 2010-02-05
Ok, I've been in the windows world way to long. My system crashed and waiting on new graphics card and hard drive to arrive so decided to test out the Ubuntu load from cd version. Btw, loving it so far and bringing back fond memories of linux and the world of free software and freedom!! Anyhow...

So, I went to intall graphics drivers for the recommended version and received the following error:
SystemError: Failed to lock /var/cache/apt/archives/lock

So did the research and it was pretty clear...
taurus
February 23rd, 2009, 08:37 AM

Do you have add/remove, update manager, or synaptic open when you try to install nvidia driver?


SuperSonic4
February 23rd, 2009, 08:44 AM

For future reference only one program can call on apt at a given time, All the ones taurus suggested use apt to function

So, did a search on apt. ughh!!!  define apt, what is apt, wtf is apt(j/k), definition of apt
Showing results 1 to 25 of 250             
                                      Search took **1.70** seconds.

[LEFT]So can someone please tell me what apt is and why you can't
run more then one instance of it as i'm trying to do mutliple things at once

I would assume there has to be multithreading in linux/ubuntu. if windows can let you update while deleteing a program and download drivers....I would assume linux and Ubuntu would too.

I'm a newbie and just getting back into the swing of linux commands and structure and have tons of reading to to. So be gentle, but point me in the right direction

What is apt??   and why can't I do multiple things in Ubuntu???

Thanks!!!!
[/LEFT]

---

### Post by mikewhatever on 2010-02-05
[What is APT.]("http://wiki.debian.org/Apt")
Sure you can multitask. It's just that APT is a backend that can only be used by one frontden, such as add/remove, update manager, or synaptic.
Windows is a different OS, and it doesn't use APT. A good Windows analogy would be trying to modify a file with several programs at the same time. Note, it has nothing to do with multitasking or multithreading.

---

### Post by pirateghost on 2010-02-05
> **mikewhatever said:**
> [What is APT.]("http://wiki.debian.org/Apt")
Sure you can multitask. It's just that APT is a backend that can only be used by one frontden, such as add/remove, update manager, or synaptic.
Windows is a different OS, and it doesn't use APT. A good Windows analogy would be trying to modify a file with several programs at the same time. Note, it has nothing to do with multitasking or multithreading.

or try to run an uninstaller and an installer that use the ms windows installer at the same time.  windows wont let you do that either.  sure some installers will work together and let you install/uninstall multiple applications at the same time, but there are a WHOLE LOT that will not.

---

### Post by nothingspecial on 2010-02-05
apt is a package manager.

syn[COLOR="Red"]apt[/COLOR]ic package manager is apt with a gui

software center is apt with a gui

update manager is apt with a gui

They are all apt

You can only run one instance of apt at a time.

You can install/remove/update as many or as few packages as you like with one instance of apt, but you can only run one apt at atime.

---

### Post by koanhead on 2010-02-05
To understand what APT is you must first know what a software "package" is in a gnu/linux distribution. In Windows, the libraries and sub-systems upon which programs depend are all the same. In gnu/linux, they can vary widely from system to system. In the absence of a monolithic system software packages need an "architecture" to make sure they get installed in the right place in the filesystem, have the right dependencies installed with them, permissions are set properly, et cetera.
    The Debian package manager is called dpkg. The packages are called .deb files. APT (A Package Tool) is a "frontend" for dpkg and for other package managers such as RPM. Ubuntu Software Centre and Synaptic are both frontends for APT.
    APT maintains a package database, and it needs to read from and write to that database when it is working on packages. It needs exclusive access to the database, because other processes writing to the database while APT is working with it can cause problems in package installation and potentially frag your system.
    As far as multitasking, not only *can* you do more than one thing at a time, your computer *always is* (unless you're somehow stuck in runlevel 2, in which case you would have lots more to complain about ;^)
    Not only can you multitask effectively (linux had preemptive multitasking before any consumer version of Windows) but you have lots more space to do it in, although I never used the extra desktops myself until I got a widescreen monitor...

---

