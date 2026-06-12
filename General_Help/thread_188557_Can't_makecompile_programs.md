---
title: "Can't make/compile programs"
date: 2006-06-04
forum: General Help
---

### Post by badrad on 2006-06-04
Hey, newbie Ubuntu user here.

One of the things that put me off the most switching to linux was I knew from previous exploits that installing apps could be a pain. I heard its really slick now, and sure enough using Add/Remove is painfully easy in Ubuntu.

Unfortunately still when you have to download things off of websites you never get binaries only source. Screw it, I say to myself, it's time I learned.

I don't know if I am doing anything wrong or if something is broken, but I can't seem to make anything. For example. I wanted the last.fm plugin for XMMS. So I download it, for the record its here:
[http://www.last.fm/help/plugin/download.php?id=7](http://www.last.fm/help/plugin/download.php?id=7)

It's instructions say to execute

```
./configure
make
make install
```

And here is what I get when I do so in my terminal:

```
cody@cody-desktop:~$ cd xmms
cody@cody-desktop:~/xmms$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
cody@cody-desktop:~/xmms$ make
bash: make: command not found
cody@cody-desktop:~/xmms$ make install
bash: make: command not found
```

Now I don't know if Ubuntu just isnt set up to do this (sounds unlikely), if I am doing something wrong, or if this is a bug.

I have also tried making ZSNES, Mame, and something else I forget.

Thanks for any help!

---

### Post by Sutekh on 2006-06-04
When compiling programs you need basic tools like a compiler (GNU C Compiler - gcc) and the make tool.

The build-essential package contains the programs you need
```
sudo apt-get install build-essential
```
This link is a good resource for installing too

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

---

### Post by givré on 2006-06-04
And if it asks for librairie you already have, install the -dev version via synaptic

---

