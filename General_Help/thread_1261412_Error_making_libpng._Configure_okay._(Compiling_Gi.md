---
title: "Error making libpng. Configure okay. (Compiling Gimpshop)"
date: 2009-09-08
forum: General Help
---

### Post by dragon4chen on 2009-09-08
Hello, as you can tell I am a newbie here. Just started using Ubuntu as a learning process for my linux classes this fall. Anyway, I spent half the day trying to install Gimpshop and it turns out I need GTK+ before I work on Gimpshop. As part of installing GTK+ I need to get all the other dependencies as instructed by this guide [here]("http://ubuntuforums.org/showthread.php?t=529448"): 

Everything was going smooth until the libpng part to install Cairo. I downloaded the latest tar.gz  as well as several old ones to try but all of them give me this error duing 'make' process: 
> 
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../../lib/libz.a(crc32.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../../lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libpng12.la] Error 1
make[1]: Leaving directory `/home/dragon4chen/Desktop/libpng-1.2.29'
make: *** [all] Error 2"./configure --prefix=/usr" went fine but it just keep getting stuck at make part. I tried "make check" and comes out same thing.
I don't know what to make of it :confused:. I've searched everywhere (or maybe I don't know where to search) for the solution but nothing has helped. 

Thanks in advance for your time and your help. Hope to hear soon.

---

### Post by andrew.46 on 2009-09-08
Hi dragon4chen,

I wonder if there is an easier way to do this? I believe Gimpshop is simply a slightly hacked version of Gimp so you *might* be able to assemble all of the required dependencies by:

```
sudo apt-get build-dep gimp
```

I have not tested this myself but I believe it might make your life a lot easier :).

Andrew

---

