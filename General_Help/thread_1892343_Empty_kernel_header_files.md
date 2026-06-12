---
title: "Empty kernel header files"
date: 2011-12-07
forum: General Help
---

### Post by jssilva on 2011-12-07
Hi,

I'm trying to compile pvrusb2 driver but I get:

```
fatal error: tda18271.h: No such file or directory

```So I went to investigate and saw that all the header files are empty (0 bytes) in the directory:
```
/usr/src/linux-headers-3.0.0-13-generic/include/config/media/tuner

```Of course I have installed linux-headers. I also checked in the directories of older kernels and the situation is the same. Even in a Debian installation that I have elsewhere.

So, is this normal? Shouldn't the headers be there? Better yet, please point me to a work-around.

Rgds,
jss

---

### Post by bluexrider on 2011-12-07
the real kernel is in the /boot directory

---

### Post by jssilva on 2011-12-07
Thanks for replying.

In /boot, you mean the compiled kernel, right? That's not what I need.

Specifically, where can you find the header file tda18271.h in /boot?

jss

---

### Post by bluexrider on 2011-12-07
> **jssilva said:**
> Thanks for replying.

In /boot, you mean the compiled kernel, right? That's not what I need.

Specifically, where can you find the header file tda18271.h in /boot?

jss

/usr/sfc/linux_headersxxxxxxx.generic/include/config/media/tuner

---

### Post by jssilva on 2011-12-07
But that's exactly what I started to say, the files are there but they are all empty; perhaps I couldn't make myself clear.

Look at the sizes:
```
# ls -l /usr/src/linux-headers-3.0.0-13-generic/include/config/media/tuner
total 0
-rw-r--r-- 1 root root 0 2011-11-02 20:02 max2165.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 mc44s803.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 mt2060.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 mt20xx.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 mt2131.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 mt2266.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 mxl5005s.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 mxl5007t.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 qt1010.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 simple.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tda18212.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tda18218.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tda18271.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tda827x.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tda8290.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tda9887.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tea5761.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 tea5767.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 xc2028.h
-rw-r--r-- 1 root root 0 2011-11-02 20:02 xc5000.h

```I think i'd better fill a bug report for this. Thanks anyway for your time.
jss

---

### Post by bluexrider on 2011-12-07
I have 1 files under that directory /usr/src/linux-headers-2.6.38-13-generic/include/config/media/tuner/tda18271.h

it appears empty but I am not sure because its a C/C++ file

---

### Post by salemboot on 2012-01-02
Install the kernel sources.

Then try somthing like #include "/usr/src/linux-source-2.6.38/include/config/media/tuner/tda18271.h"


Having the same problem.


These guys seem to think it's because nothing changed between versions.  But I don't think that is it.

[http://us.generation-nt.com/answer/packages-linux-headers-3-0-0-1-686-pae-linux-headers-3-0-0-1-common-why-such-way-help-204747571.html](http://us.generation-nt.com/answer/packages-linux-headers-3-0-0-1-686-pae-linux-headers-3-0-0-1-common-why-such-way-help-204747571.html)

---

