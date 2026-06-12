---
title: "help getting alsa to work"
date: 2006-05-14
forum: General Help
---

### Post by Polygon on 2006-05-14
Ok, so im trying to install the alsa drivers so my Sound Blaster Live 24 bit soundcard works.

i am following the instructions on this page:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106")

but im stuck on this part:

 > Now unzip and install the alsa-driver package

        bunzip2 alsa-driver-xxx
        tar -xf alsa-driver-xxx
        cd alsa-driver-xxx
        ./configure --with-cards=ca0106 --with-sequencer=yes;make;make install


cause when i do the last command (the ./configure one), i get this:

> checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


ive tried looking through sypnatic for the kernel sources for my kernel (2.6.12-10-386) but i couldent find any. Just yesterday, update notifer told me that i have like 167 updates so i downloaded and installed all of those, and i guess the new kernel 2.6.12-10-386) was a part of them. Is there any way where i can get these kernel sources so i can get these working or do i need to go back to the kernel that got installed when i first installed ubuntu?

thanks!

---

### Post by Ramses de Norre on 2006-05-14
Maybe this will help: ```
sudo aptitude install linux-headers-`uname -r` linux-kernel-headers
```

---

### Post by Polygon on 2006-05-14
never mind, ubuntu came with it installed. so im good now, thanks

---

