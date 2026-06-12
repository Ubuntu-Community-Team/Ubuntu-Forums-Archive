---
title: "ia64 vs amd64"
date: 2012-07-26
forum: General Help
---

### Post by asdfA on 2012-07-26
Hello - I noticed that some Ubuntu packages have an architecture of "ia64" and some Ubuntu packages have an architecture of "amd64". I've noticed that some packages have download options with both "ia64" and "amd64", some packages have download options with only "amd64" and there may be other variations.

I'm assuming that "ia64" is for 64-bit Intel chips and "amd64" is for 64-bit AMD chips.  However, I'm trying to download Aptitude as a package installation manager and "amd64" is the only architecture download option (no "ia64"). So will an "amd64" package work on a laptop with an Intel 64-bit chip?  Is "amd64" compatible with Intel 64-bit chips but simply optimized for AMD 64-bit chips?

From what I understand, Aptitude is a leading package installer for Ubuntu so I'd be surprised if an Aptitude package was not available for install on a machine wih an Intel 64-bit chip.

---

### Post by Grenage on 2012-07-26
AMD64 can be misleading; Intel also use AMD's x64 processes, so for a 64-bit CPU at home - you'll want AMD64 packages.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by techvish81 on 2012-07-26
any 64bit package will work in any 64 bit processor regardless of intel or amd. 
amd64 stands for 64bit which is first developed by amd and then followed by intel.

---

### Post by asdfA on 2012-07-26
> **techvish81 said:**
> any 64bit package will work in any 64 bit processor regardless of intel or amd. 
amd64 stands for 64bit which is first developed by amd and then followed by intel.

So why are both ia64 and amd64 architecture downloads listed for some packages?

---

### Post by Grenage on 2012-07-26
> **asdfA said:**
> So why are both ia64 and amd64 architecture downloads listed for some packages?

ia64 is for Intel Itanium processors.  If you don't know what they are, trust me, you don't have one.

---

