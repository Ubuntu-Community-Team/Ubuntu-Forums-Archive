---
title: "64 bit Virtual Machine in 64 bit Ubuntu"
date: 2011-02-03
forum: General Help
---

### Post by MrRichard on 2011-02-03
Hi, I was looking forward to try out Natty A2 on my 64 bit Ubuntu 10.10, but I can't figure out how to install a 64 bit guest. An error like, "this requires an x86-64 CPU, but only detected an i686. Please use a kernel appropriate for your CPU." On the Virtualbox website, it says:
"The package architecture has to match the Linux kernel architecture, that is, if you are running a 64-bit kernel, install the appropriate AMD64 package (it does not matter if you have an Intel or an AMD CPU). Mixed installations (e.g. Debian/Lenny ships an AMD64 kernel with 32-bit packages) are not supported. To install VirtualBox anyway you need to setup a 64-bit chroot environment."

I've searched other posts with no luck. Any suggestions would be greatly appreciated :).

---

### Post by MrRichard on 2011-02-03
I've read up on some old posts that said there Virtualbox doesn't support 32 bit guests. Has that changed since 2008?

---

### Post by bhaverkamp on 2011-02-03
[http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/](http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/)

More likely you host does not support VT. Not sure about virtualbox but without VT supporting 64 bit quests is not possible. I ran into this. Not all 64 bit capable CPUs support VT.

Not really a big deal; not much advantage in running 64 bit quests.

---

### Post by MrRichard on 2011-02-04
Okay then, thanks for clarifying that. I have an aging Pentium dual core e2200. I was expecting performance gains with 64 bit, oh well :rolleyes:.

---

