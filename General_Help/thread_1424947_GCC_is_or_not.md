---
title: "GCC: is or not"
date: 2010-03-08
forum: General Help
---

### Post by felix-leg on 2010-03-08
when I've try to install from sources, the *configure* tells me there is no gcc on my system:> ...
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
...but *apt-get* refuses to install gcc because "it is already installed" :???: 
WTF?

---

### Post by zouriel on 2010-03-08
What are you trying to install... and is g++ showing installed?

---

### Post by richardjh on 2010-03-08
From the output you posted:

```
...
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
**checking whether we are using the GNU C++ compiler... no**
...
```

This is complaining that g++ is not installed. You probably do have gcc installed but not g++ installed.

Try
```

sudo apt-get install g++
```

and then running the configure again.

---

### Post by falconindy on 2010-03-08
What you want is to install the 'build-essential' package.

---

### Post by felix-leg on 2010-03-09
> **richardjh said:**
> ...[cut]...
Try
```

sudo apt-get install g++
```and then running the configure again.
I thought about this too, but it refuses to install g++ :???:.

EDIT: Synaptic does it too and adds "is not intended to be installed" *<total confusion>*

---

### Post by gmargo on 2010-03-09
Please show the exact message that apt-get (or aptitude) gives you.

---

### Post by mc4man on 2010-03-09
If you can't get this squared away then you may also wish to post/link what source you're trying to build, it **may **be it requires a gcc/g++ version different than what's installed and is failing to tell you  - just saying instead that it can't be found..

---

