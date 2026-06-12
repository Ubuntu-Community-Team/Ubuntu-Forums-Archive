---
title: "trying to install i386 library"
date: 2010-09-09
forum: General Help
---

### Post by dallyt on 2010-09-09
HI everyone,

I am trying to install the following libraries on my 64 bit system as I am using a program that needs these. Can anyone tell me how to get the following:

zlib.i386
       libXi.i386
       libXtst.i386
       libXaw.i386

---

### Post by brdido on 2010-11-24
Hi all.
I have the same problem.

Newbler (gsAssembler by Roche) needs these packages for installing.

My desktop had no problems in find such packages, but I can't find those in my server.

---

### Post by Bionic_Beefpile on 2011-01-22
You can get these by installing wine.

```
sudo apt-get install wine
winecfg
./setup.sh # For Newbler
```

---

