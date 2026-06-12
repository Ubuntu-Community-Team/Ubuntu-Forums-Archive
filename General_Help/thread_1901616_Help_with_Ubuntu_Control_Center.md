---
title: "Help with Ubuntu Control Center"
date: 2011-12-28
forum: General Help
---

### Post by mortimor on 2011-12-28
Hey guys, I am trying to install Ubuntu control center but when I go to their website ([http://code.google.com/p/ucc/](http://code.google.com/p/ucc/)) it gives me a 403 error.  The reason I am trying to get UCC is to switch my laptop's GPU to my low performance chip instead.  If anyone has the deb for UCC or knows anything about this please let me know, thanks

Stephen.

---

### Post by 2F4U on 2011-12-29
I got onto this site

[http://sites.google.com/site/ubuntucontrolcenter/](http://sites.google.com/site/ubuntucontrolcenter/)

which then points to this site

[http://www.ctic.com.br/software/ucc](http://www.ctic.com.br/software/ucc)

Unfortunately, the site is in a language I can't read, but the site has download links for 32 bit

[http://www.easy-share.com/1915871724/ucc061_i386.deb](http://www.easy-share.com/1915871724/ucc061_i386.deb)

and 64 bit versions

[http://www.easy-share.com/1915871596/ucc061_amd64.deb](http://www.easy-share.com/1915871596/ucc061_amd64.deb)

---

### Post by mortimor on 2011-12-29
The 64 bit file got deleted and their google code page is down.
If anyone has ubuntu control center 64 bit deb please let me know.

---

### Post by naviathan on 2012-01-08
Anyone?  Please?  I want try the vga switching part of it and I cant figure out how to compile the source.  Theres no makefile...

---

### Post by collisionystm on 2012-01-18
the source file is just a bunch of assembly code. I am not exactly sure how to put it together.

However in the source file, there are the scripts for switching the GPU's. Ill attach them.

The highgpu.sh and lowgpu.sh are the ones you want for graphics switching.

---

### Post by Songer on 2012-02-02
Hello,

I'm new in linux, so I'm still learning it =)... I saw that UCC is a great thing for starters, but I've searched all over the internet and I can't get valid UCC download for 64 bit version. I actually need it for vgaswithceroo too (and to see and learn more stuff =). Any help please?

My system:
Ubuntu 10.10 64 bit
Kernel:
2.6.35-32-generic
Computer:
Laptop Lenovo G770, Intel i5 (2. gen.), 4Gb of ram, hybrid graphics: Ati HD6650M and Intel HD3000.

And another question to collisionystm:

> the source file is just a bunch of assembly code. I am not exactly sure how to put it together.

However in the source file, there are the scripts for switching the GPU's. Ill attach them.

The highgpu.sh and lowgpu.sh are the ones you want for graphics switching.

I've downloaded your scripts but I don't know how to use it =/. Can you shortly explain how to use your script?

Thank you all for help and sorry for my bad english =).

---

### Post by holycow131415 on 2012-02-02
The power of google search compels you all!

64 bit
[http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_amd64.deb](http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_amd64.deb)

32 bit
[http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_i386.deb](http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_i386.deb)

I figured it would be on a mirror still.

You still need to install fonts and stuff
[http://www.ubuntugeek.com/ubuntu-control-center-ucc-simple-tool-for-ubuntu-administration.html](http://www.ubuntugeek.com/ubuntu-control-center-ucc-simple-tool-for-ubuntu-administration.html)

---

### Post by collisionystm on 2012-02-02
> **holycow131415 said:**
> The power of google search compels you all!

64 bit
[http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_amd64.deb](http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_amd64.deb)

32 bit
[http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_i386.deb](http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_i386.deb)

I figured it would be on a mirror still.

You still need to install fonts and stuff
[http://www.ubuntugeek.com/ubuntu-control-center-ucc-simple-tool-for-ubuntu-administration.html](http://www.ubuntugeek.com/ubuntu-control-center-ucc-simple-tool-for-ubuntu-administration.html)



11.10 asks for simple-ccsm

get it here 

[http://packages.ubuntu.com/natty/all/simple-ccsm/download](http://packages.ubuntu.com/natty/all/simple-ccsm/download)

^ it says natty but should work.

---

### Post by BillaSong on 2012-02-05
> **holycow131415 said:**
> The power of google search compels you all!

64 bit
[http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_amd64.deb](http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_amd64.deb)

32 bit
[http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_i386.deb](http://mirror.alz3abi.com/index.php?dir=linux/Applications/&file=ucc_02_i386.deb)

I figured it would be on a mirror still.

You still need to install fonts and stuff
[http://www.ubuntugeek.com/ubuntu-control-center-ucc-simple-tool-for-ubuntu-administration.html](http://www.ubuntugeek.com/ubuntu-control-center-ucc-simple-tool-for-ubuntu-administration.html)

Thank you all for your help, specially you holycow =)... I were searching on the google for few days but I haven't found any working link for it. But I admit that I wasn't looking for older versions such as one you gave (v0.2) =).

But because of installing and uninstalling fglrx (open-source ATI driver in "Additional drivers") I've lost directory /sys/kernel/debug/vgaswitcheroo file and cuz' of that my switcheroo isn't working at all... So I've decided that I will reinstall ubuntu and switch it with 32bit version, because I don't have more than 4Gb of ram and it is easier to find stuff for 32bit version, for example UCC v0.61 on link:

[http://www.ctic.com.br/software/ucc](http://www.ctic.com.br/software/ucc)

At the end there is DL link for 32bit and 64bit (but unfortunately 64bit link doesn't work).

Oh and just for help if anyone needs more info how to easily use vgaswitcheroo with scripts, here is the link =):

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

Thank you all =)

---

