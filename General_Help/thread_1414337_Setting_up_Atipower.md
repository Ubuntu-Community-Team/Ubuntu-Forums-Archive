---
title: "Setting up Atipower"
date: 2010-02-23
forum: General Help
---

### Post by Sausage on 2010-02-23
I'm having problems building and installing Atipower to overclock my ati hd2400pro. Rovclock and Ati Overdrive don't work, I've tried. Hopefully a nobrainer for most of you so I come to you in hopes of keeping my sanity and learning something in the process. :)

I got the .tar from [here]("http://websupport.sk/~stanojr/projects/atipower/").
The contents of the folder when extracted:
```
atiddx_extensions.h       ATITVOExtensions.h  fglrx_dm_proto.h   LICENSE.GPL
atiddx_extension_tvout.h  BoardInfo.h         FGLRXExtensions.c  LICENSE.QPL
atipower.c                DualScreenPage.h    FGLRXExtensions.h  Makefile
ATITVOExtensions.c        extutil.h           fglrx_pp_proto.h   TVOExt.h
```

Now, from my (lacking) linux knowledge I gathered that I need to use "make" to make the packages, but alas, this is what I get:

> lennart@Kast:~/Downloads/atipower-0.1$ sudo make
gcc -c -g -O2 -fno-strength-reduce -funsigned-char -Dlinux -DFGLRX_USE_XEXTENSIONS -DFGLRX_OGL_INFO -I/usr/X11R6/include -I. -I./include_dummy FGLRXExtensions.c
FGLRXExtensions.c:19:37: error: X11/extensions/xf86misc.h: No such file or directory
FGLRXExtensions.c:20:39: error: X11/extensions/xf86mscstr.h: No such file or directory
make: *** [all] Error 1

---

### Post by tom4everitt on 2010-02-23
Telling from the error messages, you are lacking something like X11/extensions/xf86misc.h

Hence, run 

sudo aptitue search xf86misc

(or use apt-cache search if you prefer apt-get).

You will see a list of some packages. Run 

sudo aptitude install <name-of-suitable-packages>

to install them (make sure you install the package ending with -dev, its header files needed for compiling stuff yourself).

Try compiling again (and fix the next depency ;))

EDIT: Oh, and don't worry about installing a few too many, it only costs disk space ;)

---

### Post by Sausage on 2010-02-23
Well I installed the packages and looks like it made some progress
```
lennart@Kast:~/Downloads/atipower-0.1$ sudo make
gcc -c -g -O2 -fno-strength-reduce -funsigned-char -Dlinux -DFGLRX_USE_XEXTENSIONS -DFGLRX_OGL_INFO -I/usr/X11R6/include -I. -I./include_dummy FGLRXExtensions.c
gcc -c -g -O2 -fno-strength-reduce -funsigned-char -Dlinux -DFGLRX_USE_XEXTENSIONS -DFGLRX_OGL_INFO -I/usr/X11R6/include -I. -I./include_dummy atipower.c
atipower.c: In function ‘main’:
atipower.c:14: warning: incompatible implicit declaration of built-in function ‘printf’
atipower.c:44: warning: incompatible implicit declaration of built-in function ‘printf’
atipower.c:45: warning: incompatible implicit declaration of built-in function ‘exit’
atipower.c:56: warning: incompatible implicit declaration of built-in function ‘printf’
atipower.c:58: warning: incompatible implicit declaration of built-in function ‘printf’
atipower.c:59: warning: incompatible implicit declaration of built-in function ‘exit’
gcc FGLRXExtensions.o atipower.o -lX11 -lXext -o atipower

```

And now the folder contains:
```
atiddx_extensions.h       atipower.o          DualScreenPage.h   FGLRXExtensions.h  LICENSE.QPL
atiddx_extension_tvout.h  ATITVOExtensions.c  extutil.h          FGLRXExtensions.o  Makefile
atipower                  ATITVOExtensions.h  fglrx_dm_proto.h   fglrx_pp_proto.h   TVOExt.h
atipower.c                BoardInfo.h         FGLRXExtensions.c  LICENSE.GPL
```

So what happens now? My knowledge at this point is pretty much 0.

---

### Post by tom4everitt on 2010-02-23
So seems like the build was successful. Sometimes you're able to run 

sudo make install

at this point, for an automatic installation. In your case I would first try to launch whatever you think you have built with ./atipower. My experience tells me that its an executable (does it show up in green when you list in terminal?)

Obviously you run ./atipower after cd:ing into the directory.

---

### Post by Sausage on 2010-02-23
I have tried doing make install before and I always get
```
lennart@Kast:~/Downloads/atipower-0.1$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

And yeah the atipower file is green.
How exactly would i run it?

---

### Post by tom4everitt on 2010-02-24
As I said, you cd into the directory (which you obviously know how to since you manage to do make). 

Then you just run:

./atipower

( '.' is simply for the current directory, so you say run the file atipower in this directory by that. You could also run it from anywhere by running 

/home/user/Atipower/atipower

given that is its path.)

---

### Post by Sausage on 2010-02-24
Well, that I tried and I get
```
lennart@Kast:~/Downloads/atipower-0.1$ ./atipower
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  13 ()
  Serial number of failed request:  10
  Current serial number in output stream:  10
```

---

### Post by tom4everitt on 2010-02-24
[http://websupport.sk/~stanojr/projects/atipower/](http://websupport.sk/~stanojr/projects/atipower/)
[http://www.phoronix.com/scan.php?page=article&item=675&num=1](http://www.phoronix.com/scan.php?page=article&item=675&num=1)

I don't think this is a build issue anymore. You are supposed to use it the way you do, see link 2. 

Are you sure you have the right kind of ATI card? The right driver? I'm sorry but I know way too little about this program and ATI linux drivers help you much here I feel.

---

### Post by Sausage on 2010-02-24
Well I'm pretty sure its the only app that should support my card because rovclock is for older cards and overdrive only works starting from hd2600. My card ( hd2400pro ) SHOULD be supported but I can't find anything about the atipower app except those two sites and they don't really give out much information regarding that matter. 

I'm using the ati fglrx drivers, so the drivers aren't the issue.
I think I'll just give up since its not really a gaming card anyway and I need an upgrade, its not worth the hassle. 

Still, thanks for your help, even though I didn't get it working you surely saved me from a lot of headache. :)

---

### Post by tom4everitt on 2010-02-24
Allright, too bad it didn't work out for you. 

You did succesfully compile the source code and fix necessary depencies, however. And to launch an executable file. Two quite essential parts of linux knowledge really :)

Its quite often like that I think. You try to do something, and end up learning something completely different. 

See you around

/Tom

---

### Post by Mark Phelps on 2010-02-24
Do you know for sure if you're running the ATI drivers?

Since the HD 2400 is not supported under the current ATI drivers, it's likely that the tool you want to use won't work, either.

---

### Post by Sausage on 2010-02-24
Yeah I'm sure since I downloaded the driver by selecting my card from the "Download drivers" list. 

```
lennart@Kast:~$ lspci | grep VGA
06:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon **HD 2400 PRO**]
lennart@Kast:~$ grep 'Monitor name' /var/log/Xorg.0.log
(II) **fglrx**(0): Monitor name: SyncMaster

```

---

