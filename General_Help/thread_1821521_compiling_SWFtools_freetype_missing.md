---
title: "compiling SWFtools: freetype missing?"
date: 2011-08-09
forum: General Help
---

### Post by pe7er on 2011-08-09
I hope that this is the right board for this question.

I am trying to install (compile from source) SWFtools at my Ubuntu 10.10 from the description at [http://wiki.swftools.org/index.php/Installation](http://wiki.swftools.org/index.php/Installation)

With ./configure I got a couple of errors regarding zlib and missing libraries.
Thanks to [http://fixunix.com/debian/246537-need-zlib-compile-swftools.html#post652955](http://fixunix.com/debian/246537-need-zlib-compile-swftools.html#post652955) I was able to find the missing zlib libraries using
```
apt-cache search --names-only zlib.*-dev
zlib1g-dev - compression library - development

```

Thanks to [http://permalink.gmane.org/gmane.comp.tools.swftools.general/1922](http://permalink.gmane.org/gmane.comp.tools.swftools.general/1922) I was able to install the needed image libraries with
```

sudo apt-get install libpng12-dev
sudo apt-get install libgif-dev
sudo apt-get install libjpeg62-dev
```

However, after that I still get the error that **freetype** is missing
```
checking for missing libraries...  freetype
***************************************************
* The following headers/libraries are missing:  freetype
* Disabling pdf2swf tool...
***************************************************
configure: creating ./config.status
config.status: creating Makefile.common
config.status: WARNING:  'Makefile.common.in' seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating lib/action/Makefile
config.status: creating src/Makefile
config.status: creating swfs/Makefile
config.status: creating lib/readers/Makefile
config.status: creating config.h
config.status: config.h is unchanged

```

When I try to install freetype using ```
sudo apt-get install freetype
``` I get the following error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package freetype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'freetype' has no installation candidate
```

I guess that the freetype library is not in the repository anymore. 
How can I install it so that I can compile SWFtools ?
Thanks in advance!

---

### Post by Kira_Belka on 2011-08-09
> **pe7er said:**
> 

When I try to install freetype using ```
sudo apt-get install freetype
``` I get the following error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package freetype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'freetype' has no installation candidate
```


how about apt-get install freetype* ?

---

### Post by pe7er on 2011-08-09
> **Kira_Belka said:**
> how about apt-get install freetype* ?
Thanks very much Kira!
You've solved my error with freetype!

When I run the configure script (with "./configure") I get a warning that " 'Makefile.common.in' seems to ignore the --datarootdir setting". Do you know if that might give problems?
```
configure: creating ./config.status
config.status: creating Makefile.common
config.status: WARNING:  'Makefile.common.in' seems to ignore the --datarootdir setting
config.status: creating Makefile
```

After that I tried "make" and I got the error "g++: command not found".
I solved that with ```
sudo apt-get install g++
```

Now there seems to be one error that keeps me from finishing the "make" process: ```
cd src;make all
make[1]: Entering directory `/home/pe7er/swftools/swftools-0.9.1/src'
gcc -DHAVE_CONFIG_H wav2swf.o -o wav2swf ../lib/librfxswf.a ../lib/libbase.a -L/usr/local/lib -lungif -ljpeg -lz -lm  -lfreetype -lz
debug enabled, not stripping wav2swf
gcc -DHAVE_CONFIG_H png2swf.o -o png2swf ../lib/librfxswf.a ../lib/libbase.a -L/usr/local/lib -lungif -ljpeg -lz -lm  -lfreetype -lz
png2swf.o: In function `MovieAddFrame':
png2swf.c:(.text+0x1420): undefined reference to `swf_SetJPEGBits2'
collect2: ld returned 1 exit status
make[1]: *** [png2swf] Error 1
make[1]: Leaving directory `/home/pe7er/swftools/swftools-0.9.1/src'
make: *** [all] Error 2
```
Do you know how to fix that? 
I'll try to find some solution with google...

---

### Post by tsarv on 2011-10-23
I solved this by typing:

make clean


and then:

make

---

