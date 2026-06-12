---
title: "GCC does not find header files"
date: 2006-02-27
forum: General Help
---

### Post by EMG on 2006-02-27
Hi,

My Ubuntu 5.10 is missing C and C++  header files, apparently.
Manually looking for them does not find the right files:

# find / | grep stdio.h
/usr/lib/perl/5.8.7/CORE/nostdio.h

I have installed gcc and g++ packages with synaptic. I dont have much experience with gcc package sets for Linux (I only used gcc on MinGW for Windows before). I tried looking for them myself on synaptic, but I couldnt figure out the right names.

Could someone kindly tell me what packages I am still missing?

Thanks in advance, and excuse my poor English.

---

### Post by LordBug on 2006-02-27
You need to either install the linux headers or a kernel source tree.  Both should be in Synaptic.

---

### Post by EMG on 2006-02-27
Thanks for the advice, but it doesnt work yet :confused: 

I have just installed these packages with synaptic:

linux-386
linux-headers-2.6.12-10
linux-headers-2.6.12-10-386
linux-headers-386
linux-kernel-headers
linux-source-2.6.12
linux-tree
linux-tree-2.6.12

Thanks in advance

---

### Post by taurus on 2006-02-27
Maybe you need to install the build-essential,

```

sudo apt-get install build-essential

```

---

### Post by EMG on 2006-02-27
build-essential fixed all C and C++ headers, thank you very much!

---

