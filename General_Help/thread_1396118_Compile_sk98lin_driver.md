---
title: "Compile sk98lin driver"
date: 2010-02-01
forum: General Help
---

### Post by andreas99 on 2010-02-01
Hello World!

I have a Marvell Yukon 88E8053 PCI-X lan card. The drivers included with mythbuntu was the sky2 driver, which crashed on me. So i found that i should have the sk98lin from Marvell installed.
So i downloaded the driver.  
Modded install.sh with #!/bin/bash, so now the script runs.
I choose to install the driver. But i am always stuck on:
Check modpost availability (not available)
The installer says to look in /usr/src/linux/scripts/mod for the files modpost.c and the excutable modpost.
I have downloaded my kernel-headers and made a "ln -s headersxxx linux".
The output in that directory is:
/usr/src/linux/scripts/mod# ls
elfconfig.h  file2alias.c  mk_elfconfig    modpost.c  sumversion.c
empty.c      file2alias.o  mk_elfconfig.c  modpost.h  sumversion.o
empty.o      Makefile      modpost         modpost.o

So the files are there, i don't get what i'm doing wrong? Someone can help me?

---

### Post by mathia on 2011-03-30
Hi,
 
 **[B]Installing Marvell Yukon driver on Ubuntu**:[/B]
 
 Please install the following driver as follows:
 [http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "e.g. 88E8053 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - v10.87.3.3
 
  $ sudo bash ./install.sh
 
 and let me know if it works.
 
 Have a lot of fun ...:razz:

---

### Post by foresto on 2011-10-26
Rather than compiling it yourself, you might want to use the package I built for sk98lin.  Announcement here:
[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

