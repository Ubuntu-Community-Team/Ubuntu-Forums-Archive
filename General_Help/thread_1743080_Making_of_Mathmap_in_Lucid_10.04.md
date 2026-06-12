---
title: "Making of Mathmap in Lucid 10.04"
date: 2011-04-29
forum: General Help
---

### Post by Naggobot on 2011-04-29
Important:
If this is your first time compiling something then stop and do something else. I can not guarantee the accuracy or applicability of the information below for any other case than what is described below. Also based on previous I assume that the reader is familiar with linux to some extent and the below text is not formulated for high standard.

The story:

I wanted to compile Mathmap 1.3.5 plugin for Gimp version 2.6.11. Turned out it was not straight forward.  One reason was that I could not find anything recent about the issue so I decided to post my experiences here. If you benefit from this but have a bit different experience or find that something is not needed then post it here for others to see and learn. 

Previous thread / tutorial is fro year 2007. 

[http://ubuntuforums.org/showthread.php?t=433976&highlight=mathmap](http://ubuntuforums.org/showthread.php?t=433976&highlight=mathmap)

also this helped

[http://groups.google.com/group/mathmap/browse_thread/thread/f237e1fe7af4bfd?pli=1](http://groups.google.com/group/mathmap/browse_thread/thread/f237e1fe7af4bfd?pli=1)

A file named INSTALL  is located in the mathmap-1.3.5 directory. I strongly suggest that you read it and install first everything it says or anything you might guess is the closest alternative. In addition to what the INSTALL tells to install I also installed following packages. I do not know if all of them were really necessary since some of them are from the year 2007 thread.   

Packages
- libgimp2.0-dev
- libgtksourceviewmm-2.0-dev
- flex
- bison
- libtool

When running the ```
make
``` for the first time in to the directory 

> ~/mathmap-1.3.5$compiler returned an error

```
make[2]: Entering directory `/home/acer5020/mathmap-1.3.5/libnoise/noise/doc'
`which doxygen` Doxyfile
/bin/sh: Doxyfile: not found
make[2]: *** [html] Error 127
make[2]: Leaving directory `/home/acer5020/mathmap-1.3.5/libnoise/noise/doc'
make[1]: *** [doc] Error 2
make[1]: Leaving directory `/home/acer5020/mathmap-1.3.5/libnoise/noise'
make: *** [libnoise] Error 2

```

if you get this cd to 

```
:~/mathmap-1.3.5/libnoise/noise/doc$
```open readme and do what it says i.e. copy  the following files from the htmldata into the html subdirectory:
- background.png
- doxygen.css
- libnoise.png

I used Nautilus for this.

This seems like a stupid and unnecessary thing to do since files are already there but I quess it helps for some reason. At least it does not hurt. After copying the files run 

```
make 
```in  the 

```
:~/mathmap-1.3.5/libnoise/noise/doc$
```directory

then

```
cd ..
```to 

```
~/mathmap-1.3.5/libnoise/noise$ 
```run 

```
make
```then

```
cd ..
```and

```
cd ..
```and 

```
make
```After this the make should be ready and error free if you had the same problem set as I had. I do not give any advise on the install since I used Checkinstall so that I can track the installation from Synaptic. If you want to use Checkinstall and you have it installed then just type

```
checkinstall
```in the mathmap directory. For me the Checkinstall prompted about some files and at this point I messed up and had to redo the installation and manually remove some symbolic link to get installation done. I suggest that you do not attempt to list the files when prompted with question. Checkinstall offers default [n] so use it and use suggested [yes] on next prompt. 

After installing the plugin worked but on the first run I had multiple errors about system finding multiple similarly named filters. Since there was a prompt for every filter I killed the app and removed the folder

/usr/share/gimp/2.0/mathmap/expressions/examples/

After this the Mathmap started with out hickups and seems to work. 
(tried and tested once so far)

---

### Post by eel on 2011-12-08
Hi

I have been trying to install mathmap for quite a while now, but i keep getting this error when running 'make' in mathmap-1.3.5: 


```
native-filters/convolve.o -c native-filters/convolve.c
native-filters/convolve.c:26:19: fatal error: fftw3.h: No such file or directory
compilation terminated.
make: *** [native-filters/convolve.o] Error 1

```

If i run make clean i see that convolve.c is in the native-filters directory, but not convolve.o. But that goes for other files in this directory as well, like cache.c. When i run make a cache.o file appears in native-filters, so i assume the same should happen for convolve.c, but it doesn't. 

I have followed your (very clear!) tutorial , and tried several other things i found on forums and blogs, but i can't seem to get past this point...

---

