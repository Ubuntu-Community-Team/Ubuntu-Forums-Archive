---
title: "error compiling ghostpdl"
date: 2010-07-07
forum: General Help
---

### Post by ibnpaul on 2010-07-07
I figured this out.  The source was looking for libXext.so in /usr/lib, but there is no file of exactly that name, so I made a symlink to libXext.so.6 with that name, problem solved!

Hello all,

I am currently on a mission to convert a PCL file to a PDF and my best hope seems to be the GhostPCL tool.  I have donwloaded the source as I cannot find a .deb for it and have attempted to compile it, but I keep getting this error:

```

writing node 'ttfonts/AntiqueOlive-Bol.ttf' len=136120
Total %rom% structure size is 5553136 bytes.
cc  -O2 -Wall -Wundef -Wstrict-prototypes -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wwrite-strings -Wno-strict-aliasing -fno-builtin -fno-common -DHAVE_STDINT_H -DHAVE_MKSTEMP -DHAVE_HYPOT -DGX_COLOR_INDEX_TYPE="unsigned long"  -DPCL_INCLUDED  -I./obj -I../gs/base  -o ./obj/gsromfs1.o -c ./obj/gsromfs1.c
./obj/echogs -w ./obj/ldall.tr -n - gcc  -L/usr/X11R6/lib -o ./obj/pcl6
./obj/echogs -a ./obj/ldall.tr -n -s ./obj/pctop.o ./obj/pxtop.o ./obj/gsargs.o ./obj/gconfig.o ./obj/gscdefs.o -s
cat ./obj/ld.tr ./obj/ldconf.tr >>./obj/ldall.tr
./obj/echogs -a ./obj/ldall.tr -s - ./obj/gsromfs1.o ./obj/plmain.o ./obj/plimpl.o  -lm -lpthread -ldl
sh <./obj/ldall.tr
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[2]: *** [obj/pcl6] Error 1
make[2]: Leaving directory `/home/ibnpaul/Downloads/Linux/Programs/System/ghostpdl-8.71/main'
make[1]: *** [pdl-product] Error 2
make[1]: Leaving directory `/home/ibnpaul/Downloads/Linux/Programs/System/ghostpdl-8.71/main'
make: *** [pcl] Error 2

```

I have also downloaded the ufwfonts package separately and unpacked it to the source directory as required before running make.

I also tried make clean and then make, to no avail.

The package comes with a makefile and does not come with a configure script, so no configure errors that I can post.

I am running 2.6.32-23-generic x86_64.

Please let me know if you need any other information, and thank you all for your help!

---

### Post by mc4man on 2010-07-07
With no configure log may take a little trial & error, start by what the error reported
```
sudo apt-get install libxext-dev
```

---

### Post by euzkoarima on 2011-07-06
I had the same problem and reading this post tried "sudo apt-get install libxext-dev"

It works ok, thanks !!

---

