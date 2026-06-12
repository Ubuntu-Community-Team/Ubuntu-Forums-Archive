---
title: "How to install zlib?"
date: 2010-07-10
forum: General Help
---

### Post by micael3000 on 2010-07-10
Hello,

I have to install zlib for running ./configure.
Can anyone help me doing this? I typed "sudo apt-get install zlib" but it doesn't work...

> configure: error: zlib library not found or incompatible, please specify the correct path with --with-zlib=DIR... stopping

Thanks.

edit: ubuntu 10.04

---

### Post by nemilar on 2010-07-10
What package are you trying to compile when you run "./configure"? 


It's likely that the package you need is in the software repositories, so you don't have to compile it manually.

---

### Post by micael3000 on 2010-07-10
eAthena (ragnarok server emulator)

edit: it does have a zlib1.dll in its main folder

---

### Post by dino99 on 2010-07-10
[http://www.eathena.ws/wiki/index.php/Installation](http://www.eathena.ws/wiki/index.php/Installation)

[http://www.axwebsolutions.com/clients/knowledgebase.php?action=displayarticle&id=32](http://www.axwebsolutions.com/clients/knowledgebase.php?action=displayarticle&id=32)

---

### Post by micael3000 on 2010-07-10
After installing zlib (from zlib website) my SO crashed. Now it doesnt start anymore... I am reinstalling...

---

### Post by micael3000 on 2010-07-10
I did all again, with an ubuntu CD i formated my computer and reinstalled ubuntu.
Then i updated it, installed yakuake and zlib ([http://www.zlib.net/](http://www.zlib.net/) I downloaded:     **zlib** source code, version 1.2.5, tar.gz format) with ./configure and make install.

When i reboot my computer, it stoped working again... (do not open login window, just go to the background image, with mouse, and stops there forever)

Does anyone know how to install zlib without crashing the whole system?

---

### Post by mortalapeman on 2010-07-12
Ok so I am having the same problem as you. I'll try this when i get home and let you know if it works.
 
[http://www.techsww.com/tutorials/libraries/zlib/installation/installing_zlib_on_ubuntu_linux.php](http://www.techsww.com/tutorials/libraries/zlib/installation/installing_zlib_on_ubuntu_linux.php)
 
In the mean time, to fix you're crashed system just follow these instructions:
 
1. Boot into recovery mode through grub and login as you're self
 
2. Go to the directory you unpacked zlib
```
cd ~/Downloads/zlib.#.#.#
```
 
3. uninstall zlib
```
sudo make uninstall
```
 
4. I'm not sure if this helps but I did it anyway
```
sudo apt-get install --reinstall zlibc zlib1g zlib1g-dev
```
 
(Off hand i think the packge is zlib1g, use apt-cache --name-only search zlib or aptitude search zlib to find the one that closely matches it and run that apt-get command)
 
This fixed my Ubuntu after I wasted my time and reinstalled my system and tried to install zlib again. So hopefully it can work for you too.

---

### Post by gargamelle on 2010-07-27
this is being chatted here as well 

[http://art.ubuntuforums.org/showthread.php?p=9628748](http://art.ubuntuforums.org/showthread.php?p=9628748)

and I have the same problem with zlib 1.2.5 and ubuntu10.04.

---

### Post by Mathew Roy on 2010-09-08
Even I had the same trouble and I had to reinstall the system 3 times. But here the solution.
Try this, it worked well with me.
go to
System->Administration->Synaptic Package Manager
search for zlib1g-dev and install the package. (My system didnot crash this time.)
Simple as that...

---

