---
title: "Do repos automatically use 64bit programs on AMD64?"
date: 2010-08-22
forum: General Help
---

### Post by vayu on 2010-08-22
Just set up my first 64bit install.  
The repositories look like the same ones as my i386 install. 
How many of the programs in the repos are 64bit?  How does it work that I don't get 32bit versions of programs? Do I have to specifically look for 64bit programs?  Do 32bit programs run as fast with 32bit libs on a 64bit system as they would on a 32bit system?

---

### Post by jpaugh64 on 2010-08-22
apt-get will automatically use binaries for your system's architecture. As far as I know, most packages available for i386 have amd64 equivalents. I tried a 64 bit install, back in 08. It worked okay, but for some programs the 64bit version seemed buggier (probably due to fewer users?), and I wasn't interested so much in being a "test case" for the developers, so I switched back to 32bit. 
(Also, I couldn't run some old DOS programs in wine because the processor doesn't support switching between long mode and virtual-86 mode.)

Hope it works well for you, friend.

---

### Post by howefield on 2010-08-22
> **vayu said:**
> How many of the programs in the repos are 64bit?

Most of them, the ones I use that don't have 64 bit versions are skype, wine, and sopcast. Flash is another until the 64 bit Adobe plugin is supported again. There's bound to be a few more.

> How does it work that I don't get 32bit versions of programs? Do I have to specifically look for 64bit programs?

No, you will get a 64 bit version if it exists, if not you'll get the 32 bit version with 32 bit libraries.

> Do 32bit programs run as fast with 32bit libs on a 64bit system as they would on a 32bit system?

With good hardware and not getting the stop watch out, can't say I've noticed any difference, ymmv.

---

### Post by hotrodder on 2010-08-22
99.99% of the software available in the repos for 64 bit is actually 64 bit software.

---

### Post by clhsharky on 2010-08-22
All distro's supporting updates(upgrades, bug fix's) is a
> "test case"
The next release will benefit from the last.

Sharky

---

