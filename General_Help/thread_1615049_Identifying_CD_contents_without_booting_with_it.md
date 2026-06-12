---
title: "Identifying CD contents without booting with it"
date: 2010-11-06
forum: General Help
---

### Post by harisund on 2010-11-06
hello !

So I have a bunch of CDs I have burnt over the past year or two, and only problem is, I would burn them, use it and forget about it. I never bothered labelling it. 

Now, I want to label them appropriately. Is there any way I can find out the following just looking at the CD contents- 

1. Distribution - lucid / karmic / etc 
2. Architecture - amd64 or i386
3. Type - server, desktop, alternate etc 

I know if I boot into the machine from the CD drive, I can find out, but I prefer not having to do that. Anyway I can do it just by mounting the CD ROM and reading the contents?

---

### Post by sikander3786 on 2010-11-06
I just had a random look at one of my discs right now and found this in the MD5SUM file. Hope it helps.

> a5a788ebc3d91f9714b27643f006ba66  ./dists/lucid/restricted/binary-i386/Packages.gz

Edit:  There is also a file named Release under Dists directory.

---

