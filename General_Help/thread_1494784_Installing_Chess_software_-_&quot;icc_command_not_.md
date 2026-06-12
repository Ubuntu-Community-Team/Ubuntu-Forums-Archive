---
title: "Installing Chess software - &quot;icc command not found&quot;"
date: 2010-05-27
forum: General Help
---

### Post by ghostcoil on 2010-05-27
I'm running ubuntu 9.10 and was trying to install some chess software - Crafty-23.2 - and i ran into some trouble. There's no configure file so i ran make:

```

sol@sol-desktop:~/Downloads/crafty-23.2$ make
make linux-64
make[1]: Entering directory `/home/sol/Downloads/crafty-23.2'
make target=LINUX \
		CC=icc CXX=icc \
		CFLAGS='-w -xP -O2 -fno-alias -prof-use -prof_dir ./profdir' \
		CXFLAGS='-w -xP -O2 -prof-use -prof-dir ./profdir' \
		LDFLAGS=' -lpthread -lstdc++' \
		opt=' -DINLINE64 -DCPUS=2' \
		crafty-make
make[2]: Entering directory `/home/sol/Downloads/crafty-23.2'
make[3]: Entering directory `/home/sol/Downloads/crafty-23.2'
icc -w -xP -O2 -fno-alias -prof-use -prof_dir ./profdir -DINLINE64 -DCPUS=2 -DLINUX -c crafty.c
make[3]: icc: Command not found
make[3]: *** [crafty.o] Error 127
make[3]: Leaving directory `/home/sol/Downloads/crafty-23.2'
make[2]: *** [crafty-make] Error 2
make[2]: Leaving directory `/home/sol/Downloads/crafty-23.2'
make[1]: *** [linux-64] Error 2
make[1]: Leaving directory `/home/sol/Downloads/crafty-23.2'
make: *** [default] Error 2

```

Sudo make yields the same results. I double checked that i've got build-essential, so i'm at a bit of a loss.

---

### Post by gmargo on 2010-05-27
Read The Fine Makefile.  You need to run "make linux" unless you have the Intel "icc" compiler.  Other adjustments may be necessary ("make linux" failed on my Hardy system.)

If you can live with the previous version, 23.1 on Lucid (22.10 on Karmic), you can install it directly from the repository.

[http://packages.ubuntu.com/search?keywords=crafty&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=crafty&searchon=names&suite=lucid&section=all)

---

### Post by ghostcoil on 2010-05-27
make linux failed on mine too - i've downloaded the older version for now and will work out what needs to be done for the new one.

thanks a lot!

---

### Post by gmargo on 2010-05-28
Easiest way to get the new one compiled would be to download the source patches from the 23.1 version and start with that.  Do an "apt-get source crafty" on a Lucid machine or download from here: [http://packages.ubuntu.com/source/lucid/crafty](http://packages.ubuntu.com/source/lucid/crafty)

---

