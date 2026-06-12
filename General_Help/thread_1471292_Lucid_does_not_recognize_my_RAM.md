---
title: "Lucid does not recognize my RAM"
date: 2010-05-03
forum: General Help
---

### Post by mgcleveland on 2010-05-03
I just upgraded from 9.10 to 10.04 this morning and half of my RAM is not recognized!

Specs: Pentium 4 2x 2.80GHz, 1001.6 MiB RAM (should be 2x this), Ubuntu 10.04.

Thanks for your help!

---

### Post by rapsodia on 2010-05-03
I having the same issue I did a fresh install and 1GB of ram is gone 

any ideas ???

---

### Post by kouter on 2010-05-03
run in terminal and paste the output please of:
```
uname -r
```

---

### Post by rapsodia on 2010-05-03
2.6.32-21-generic

---

### Post by mgcleveland on 2010-05-07
2.6.32-22-generic

---

### Post by mgcleveland on 2010-05-11
Has anyone else experienced this or have an idea why it's happening?

---

### Post by philinux on 2010-05-11
> **mgcleveland said:**
> I just upgraded from 9.10 to 10.04 this morning and half of my RAM is not recognized!

Specs: Pentium 4 2x 2.80GHz, 1001.6 MiB RAM (should be 2x this), Ubuntu 10.04.

Thanks for your help!

What does this show.

```
free -m
```

---

### Post by mgcleveland on 2010-05-13
mgcleveland@phamnuwen:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        961         39          0        179        226
-/+ buffers/cache:        555        446
Swap:         2957         26       2930

---

### Post by Sesshomurai on 2010-06-19
Lucid does not recognize my 4GB memory and only sees 3GB. A real serious problem...This was also the case with prior releases too.

---

### Post by proggy on 2010-06-19
You don`t mention if you have Ubuntu 32 or  64 bit

---

### Post by PRC09 on 2010-06-20
For the disappearing ram problem,I have never seen that one before,maybe just remove the dimms and reseat them in the sockets again.For the other problem of not seeing more than 3 gigs,if you install straight from the cd with no internet connection present during install it will install the regular kernel.If net connection is present the installer will automatically install the PAE kernel which allows you to use all your ram up to I think 64 gigs....


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by PRC09 on 2010-06-20
Edit: The above was in reference to 32bit systems....

---

### Post by megamandos on 2010-06-20
> **Sesshomurai said:**
> Lucid does not recognize my 4GB memory and only sees 3GB. A real serious problem...This was also the case with prior releases too.


you are using 32-bit, it has a memory limit of 3.5GB. install 64 bit to utilize the rest.

---

### Post by evilducy on 2010-06-23
> **PRC09 said:**
> For the disappearing ram problem,I have never seen that one before,maybe just remove the dimms and reseat them in the sockets again.For the other problem of not seeing more than 3 gigs,if you install straight from the cd with no internet connection present during install it will install the regular kernel.If net connection is present the installer will automatically install the PAE kernel which allows you to use all your ram up to I think 64 gigs....


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)


This worked on mine, I'm now running kernel 2.6.32-22-generic-pae.
My system is a AMDTruion 64 MK36, and I'm using 3.8 gig of 4.

---

