---
title: "Is there a AS400 Emulator?"
date: 2010-01-14
forum: General Help
---

### Post by gypsumwolf on 2010-01-14
Is there a AS400 Emulator for ubuntu? Or some way to set it up in VirtualBox OSE ?

---

### Post by Fire_Chief on 2010-01-14
There is the tn5250 emulator for accessing an AS/400 in the repositories.
```
sudo apt-get install tn5250
```

Cheers!

---

### Post by gypsumwolf on 2010-01-14
> **Fire_Chief said:**
> There is the tn5250 emulator for accessing an AS/400 in the repositories.
```
sudo apt-get install tn5250
```

Cheers!

Thanks, but I meant something that I can run from my personal computer to emulate the AS/400's operating system, OS/400.

---

### Post by lykwydchykyn on 2010-01-14
There's [hercules](http://www.hercules-390.org/) in the repository, but I don't know if it supports OS/400.

I think most vm's only emulate x86/x64 architectures.  qemu can emulate a variety of architectures if you install the qemu-kvm-extras package, but I don't know if any of them support OS/400.

---

### Post by gypsumwolf on 2010-01-14
This may be the best thing out there right now for this. One of my friends showed it to me: [http://www.timeshare400.com/Individuals.htm]("http://www.timeshare400.com/Individuals.htm")

---

### Post by mstephens on 2010-02-17
> **lykwydchykyn said:**
> There's [hercules](http://www.hercules-390.org/) in the repository, but I don't know if it supports OS/400.

I think most vm's only emulate x86/x64 architectures.  qemu can emulate a variety of architectures if you install the qemu-kvm-extras package, but I don't know if any of them support OS/400.

Hercules won't support AS/400 (now iSeries) as the architecture is completely different - the only real similarity is that they both natively use EBCDIC. iSeries currently runs on PowerPC as does pSeries (ex RS6000) with the interesting result that a binary compiled under AIX on pSeries can be run on iSeries without an emulation layer. Doesn't really work the other way round as although iSeries supports an AIX-like subsystem, pSeries doesn't have an equivalent i5/OS subsystem.

It would be fairly straightforward to build something that emulates an iSeries box (which would also emulate a pSeries box as they are pretty much identical at the hardware level). The problem comes when you actually want to do something with it as you would need to write new versions of i5/OS AND all the other licensed products from scratch. 

Hercules had the advantage that some early IBM system and application software fell into the public domain plus there are a large number of mainframe system programmers who know enough to write lookalikes from scratch.

The IBM midrange boxes were more aimed at the "run straight from the box" market so there isn't a huge amount of in depth knowledge about. Plus the binary compatibility which exists for the mainframe doesn't follow through on the midrange stuff - hence the iSeries can only run software compiled for System/36 by providing a System/36 emulation mode.

---

