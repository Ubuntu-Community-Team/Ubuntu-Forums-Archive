---
title: "Using apt-build, Problem with build dependencies"
date: 2009-09-23
forum: General Help
---

### Post by DevinMcElheran on 2009-09-23
I'd like to start compiling my own programs, but I don't want to  do the Gentoo thing. I like the simplicity of Ubuntu. I don't want to have to download all the tarballs and so on, I just want to be able to "apt-build install <package>" and have it done for me. The reason for this is that I have an Eeepc, which is a bit slow, especially x, and I have an Intel Q8200 quad core, and I want the most out of it. But when I try to install/compile the program, I'm missing the build dependencies, is there any way to make sure I have them before hand, like a on a Gentoo system? Any help is greatly appreciated.

---

### Post by scragar on 2009-09-23
```
apt-get build-dep **packageName**
```
Apt FTW :p

---

### Post by DevinMcElheran on 2009-09-23
So I tried it, I used Audacity for my test package, nothing major, but still needs a few libraries, and this was the output:

E: Build-dependencies for audacity could not be satisfied.

So, I'm not sure what's going on.

---

