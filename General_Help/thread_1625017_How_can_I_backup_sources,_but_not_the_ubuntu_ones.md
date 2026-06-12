---
title: "How can I backup sources, but not the ubuntu ones"
date: 2010-11-18
forum: General Help
---

### Post by nolag on 2010-11-18
I want to make a program (or script for now that I can use in one) that will backup the sources, but not the ubuntu ones. What I mean say I have ubuntu 9.04 and I want to update to 10.10, I can copy all the extra sources and add them to the sources list, but not the ones for ubuntu 9.04 (since I will have the 10.10 ones). I want to do this with a script, so it can be for backing up and automated. I would also like it to work in debian (or any spin off of including ubuntu spin offs), that way if someone is switching from one debian based distro to another it can be made easier. The only problem I am having is in knowing if the source is part of the core of the distro or not. I would combine this with one that will backup installed programs, so you could easily move them with you for an upgrade or to try a new distro :D.
 
I could sware I created this thread already (today actually) but I guess my browser did not submit it before I closed it :P.

---

### Post by papibe on 2010-11-18
Thinking in a slightly different direction, one solution would be to triple boot your system. That way, every time you boot you can choose from 9.04, 10.10 or Debian.

In order to have always your files available, you'd need to have a separate partition for /home that could be mounted by all OSes.

I hope that helps.

---

### Post by nolag on 2010-11-19
> **papibe said:**
> Thinking in a slightly different direction, one solution would be to triple boot your system. That way, every time you boot you can choose from 9.04, 10.10 or Debian.
 
In order to have always your files available, you'd need to have a separate partition for /home that could be mounted by all OSes.
 
I hope that helps.
 
I do triboot (Windows 7, ubuntu and debian) although I just started with debian.  I want to set up ubuntu, then transfer the applications I installed (like the programming IDEs, svn, compiz) to debian.  I would also like to have them backed up so that if I want to go to another computer it is easy to set up (say for a friend who uses ubuntu, mint, debian, some other debian/ubuntu derivative).  I do have a shared partition for both of them to share files on as well :).

---

### Post by dino99 on 2010-11-19
dont need to do that, its useless:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

note: sources are into /var/cache/apt/archives/

---

### Post by KeyserSoze93 on 2010-11-19
You should be able to keep your existing sources.list and just replace every instance of "lucid" with "maverick".

---

### Post by nolag on 2010-11-19
> **dino99 said:**
> dont need to do that, its useless:
 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
 
note: sources are into /var/cache/apt/archives/
 
Wait how does that make backing up sources usless?
 
> **KeyserSoze93 said:**
> You should be able to keep your existing sources.list and just replace every instance of "lucid" with "maverick".
 
Again, I would like to be able to use it with any debian based os not just ubuntu :P.  Idealy it would make switching distros and upgrading easier (as well as fresh installs), but thanks for trying :).

---

