---
title: "Windows 7 32 bit and Ubuntu 10.04 64 bit via Wubi"
date: 2010-06-17
forum: General Help
---

### Post by wmopnc on 2010-06-17
I apologize if this has been discussed as I could not find it within the forum.  I also feel like this is a silly question but I wanted to understand what the limiting factor was that would not allow me to do this, if there is one.  See below.

I have Windows 7 32 bit.  I have installed Unbuntu 10.04 32 bit vi Wubi and all is working.  I was wondering if I could install Ubuntu 10.04 with Wubi as 64 bit.  If yes, great, if not what is limiting the install?  boot loaders, etc.?...

Note:  When I ran Wubi for the first time it actually started to download the 64 bit image which made me nervous so I downloaded the 32 bit manually, blah blah blah...

Thanks in advance.

---

### Post by bcbc on 2010-06-18
There's no reason why you can't run 64 bit if your machine supports it. It doesn't matter whether your windows is 32 bit.

Wubi automatically downloads the correct version for your computer - and as you've said, it was downloading the 64-bit. So yes it should work.

I don't think you'll notice any major difference (that's my understanding since I've never run a 64bit OS) but from what I've read the performance isn't necessarily faster, the apps may be more limited, and while it supports >=4GB ram, the pae kernels do this anyway on 32bit.

---

