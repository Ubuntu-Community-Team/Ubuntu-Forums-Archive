---
title: "installing 32 bit R on 64bit Machine"
date: 2010-03-16
forum: General Help
---

### Post by swirlz on 2010-03-16
Hi all,

Here is my problem. I need to use a R (statistical software) library (FEAR) that is compiled for the 32 bit version of R.

I have a 64 bit machine and am currently running th 64 bit version of R. My question is this:

How can I install the 32 bit version of R on my machine?

Thanks in advance.

---

### Post by rnerwein on 2010-03-16
hi
i build 32 bit aps on karmic 64 too.
you have to install: sudo apt-get install ia32-libs, apt-get install gcc-4.4-multilib. works !
if you got only a single 32bit lib you can place it in /usr/lib32
good luck
ciao

---

### Post by srs5694 on 2010-03-16
There's an added twist in that the package swirlz wants to install is an R analysis package. I don't know offhand if the 64-bit version of R supports 32-bit supplemental packages. If it does, it should be possible to install the 32-bit supplemental package and it'll work normally. If not, swirlz will either have to replace the 64-bit main R package with a 32-bit version or track down a 64-bit version of the supplemental package. It may be possible to compile a 64-bit version of the package locally, but that could be a big hassle. I'm only vaguely familiar with R myself (I've installed it for a client of mine), and not at all with FEAR, so I can't offer much more precise advice.

---

