---
title: "Instillation on an old machine"
date: 2010-07-10
forum: General Help
---

### Post by 12-1-50 on 2010-07-10
I have an older machine, it has 128mb of ram, a 731mh Intel Pentium III processor, and about 36 Gigabytes of memory open on its hard drive. I was wondering if it is possible to run ubuntu or xubuntu on this machine and if I had to use any alternate method of instillation.

---

### Post by mike555 on 2010-07-10
Probably only a really small distro like "Puppy" will run good on it .

---

### Post by cascade9 on 2010-07-10
128MB is just to small for xubuntu/ubuntu. Lubuntu might just work, but it wouldnt be nice IMO. 

mike555 is right, with that level of RAM, you would need a 'light' distro.

---

### Post by nmaster on 2010-07-10
i'd say start with a minimal install: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

then use LXDE: sudo apt-get install lxde

add things as you see fit.  with such a small amount of ram, its best to start small and build it up rather than trying to start with a full desktop system. 

 i have a machine with basically the same specs (slightly less disk space, but the same RAM, and processor) and i did basically this only i started with a debian net installation.  it works great (i can even watch flash), but using an ubuntu minimal install is might be easier.  ubuntu has more software in the repos (especially if you include third party repos) and the base installation has a couple of things that you'll probably need to apt-get anyway (like sudo)

---

### Post by nmaster on 2010-07-10
> **mike555 said:**
> Probably only a really small distro like "Puppy" will run good on it .

i've done this on my old machine too (rough specs in the post above).  it ran super fast and worked well, but i didn't like being logged in as root and the package management sucks when you compare it to ubuntu/debian.

---

### Post by 12-1-50 on 2010-07-10
I think I will try ubuntu minimal

---

