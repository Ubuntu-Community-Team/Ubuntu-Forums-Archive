---
title: "Need help to get a dep working."
date: 2009-11-16
forum: General Help
---

### Post by dgrafix on 2009-11-16
Where is libstdc++5 gone for Karmic. I really need it.
I cannot seem to find anything to explain why it has gone nor how to fix it.

---

### Post by Giblet5 on 2009-11-16
It is gone because it has been superseded by libstdc++6.

Trying to run Doom3?

---

### Post by hwttdz on 2009-11-16
Or intel compiler suite.  You could try the silent install without libstdc++5 

[http://software.intel.com/en-us/articles/intel-compilers-for-linux-version-111-silent-installation-guide/](http://software.intel.com/en-us/articles/intel-compilers-for-linux-version-111-silent-installation-guide/)

But what I did was add back in some of the intrepid repositories.  I put

```
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid main restricted
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid-security main restricted
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid-security multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid-security universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid-updates main restricted
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid-updates multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ intrepid-updates universe
```

in /etc/apt/sources.list.d/intel_suite.list then you can do "sudo apt-get update", "sudo apt-get install libstdc++5", of course you only need one of these lines, but I didn't bother to establish which.  Of course, unless you live in manhattan, you should probably change the Columbia server, to one that's faster for you.

---

### Post by dgrafix on 2009-11-17
> It is gone because it has been superseded by libstdc++6 I gathered that giblet :D
Although it seems dumb to me to replace it with something that is seemingly not compatible, without leaving the old one in case it is needed.
(ps no it is not doom, it is something written in bmax)

@hwttdz: Thanks, i will try that when i get home.

---

### Post by dgrafix on 2009-11-22
Have installed V5 but it still says it is missing. Perhaps it is looking for 32bit libs.

---

### Post by hwttdz on 2009-11-22
sudo apt-get install ia32-libs

If you're installing the intel compiler suite there is an error in the detection of these libraries, so I had to install using the silent install method after installing the libraries.

---

### Post by dgrafix on 2010-01-18
I tried that it says they are already installed

---

