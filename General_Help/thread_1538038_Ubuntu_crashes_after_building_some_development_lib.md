---
title: "Ubuntu crashes after building some development libraries"
date: 2010-07-24
forum: General Help
---

### Post by Guirgis on 2010-07-24
Hello,
I'm experiencing a serious problem since Ubuntu 8.10, it keep happening on every version (now, i'm using Ubuntu 10.4), the problem is:
I'm working on a project that depends on many 3rd party projects and libraries like UniMRCP project which depends on APR, APR-util , Sofia-SIP libraries.
Also i use other libraries like CURL, SpiderMonkey, ZLib, Julius, PCRE.
After building all these libraries, most applications don't respond to anything like you cannot display a shell script or open a package manager.
After restart, I cannot login to the kernel, I just saw an empty screen. on version 9.10 i got a message says that the nautilus file manager is damaged (I can't remember exactly the error message).
It happened to me today on version 10.4, instead of desperately reinstalling Ubuntu, i messed with the libs in /usr/local/lib folder (removed all the libraries installed from my building), Surprisingly it worked, but i don't know why?
I once tried installing my project on Fedora v.12 and i didn't face this error but i don't want this to force me leave Ubuntu.

Any suggestions? Thanks in advance.

---

