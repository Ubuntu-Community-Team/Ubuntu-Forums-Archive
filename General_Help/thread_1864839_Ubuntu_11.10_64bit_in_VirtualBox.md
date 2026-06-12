---
title: "Ubuntu 11.10 64bit in VirtualBox?"
date: 2011-10-19
forum: General Help
---

### Post by QuantumMonkey on 2011-10-19
I read that you can run 64 bit OS's in VirtualBox, so I updated to the newest version, just to be sure, and tried to start the AMD64 version of 11.10. It said it needs a 64bit cpu. Uujshdnfkjsd.

I am running the AMD64 version of VirtualBox 4.1 on Ubuntu 11.04 32 bit on a 64 bit processor.

Yupp.

---

### Post by duke.tim on 2011-10-19
Your cpu needs to have virtualization support.

you can check to see if you have it by

```
egrep &#8216;(vmx|svm)&#8217; /proc/cpuinfo
```

look for vmx or svm

if you don't see vmx or svm you are out of luck, unless you change your cpu or get a new computer.
You can always use 32bit ubuntu on vbox.

[http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/](http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/)

---

