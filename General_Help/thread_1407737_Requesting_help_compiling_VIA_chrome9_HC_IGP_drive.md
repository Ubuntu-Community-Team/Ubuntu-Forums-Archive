---
title: "Requesting help compiling VIA chrome9 HC IGP drivers"
date: 2010-02-15
forum: General Help
---

### Post by TheViLliN on 2010-02-15
Hi.

Please excuse my lack of programming an compiling skill.

This is on another fresh install of Ubuntu 9.04 / updated.

I'm having a trouble seeking out all the dependencies and utilities for compiling the graphics drivers for this "Biostar P4M900-VM" motherboard.

It has the chrome9 integrated VIA graphics chipset.

I've downloaded the drivers from VIA Arena.

via-xserver-86a-50283_src.tgz 

Extracted them.

Install autoconf and build-essential.

But now when I try compiling i get

....cking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
./configure: line 11977: syntax error near unexpected token `XINERAMA,'
./configure: line 11977: `XORG_DRIVER_CHECK_EXT(XINERAMA, xineramaproto)'


I've been trying to read and find answer's.  I think it has something to with "xorg macros" module or some Xorg dev libraries but I can't seem to  find and install the correct stuff. 

Now my head hurts now.  My plan was to get this box up and going so I could continue on with the rest of my work but I've been hours searching for this.  Yeah till 4am last night.  So aside from just buying another nvidia card I would like to ask for some help please.

Any ideas?

Perhaps on a side note if anyone has a good Linux top notch programming / compiling primer thread.  That would be awesome.

---

### Post by melnijir on 2010-05-16
I am answering to an old question, but it maybe helps other people searching answer. Package xorg-dev should be enought to get these macros working.

---

