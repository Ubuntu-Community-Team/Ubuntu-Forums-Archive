---
title: "Installing Cinelerra"
date: 2011-01-14
forum: General Help
---

### Post by lhamil64 on 2011-01-14
I just installed Ubuntu 10.10 64bit using Wubi. I had 32 bit installed in a Virtual machine on Windows but I wanted to install it to my harddrive (and wubi was easiest). I'm trying to install Cinelerra following the instructions at: [http://cinelerra.org/docs/cinelerra_cv_manual_en.html#SEC13](http://cinelerra.org/docs/cinelerra_cv_manual_en.html#SEC13)

Once I get to:
autoreconf -i --force
it gives a few errors. Here's a copy and paste from the terminal:
> 
lee@ubuntu:~/hvirtual$ autoreconf -i --force
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 196.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf line 196.
Can't exec "autopoint": No such file or directory at /usr/share/autoconf/Autom4te/FileUtils.pm line 345.
autoreconf: failed to run autopoint: No such file or directory
autoreconf: autopoint is needed because this package uses Gettext


Can anyone help with this? I've tried googling but I can't find anything. Cinelerra's installation isn't very user friendly (although i was able to install it in the virtual machine previously, so I think it has to do with having 64bit)

---

### Post by sisco311 on 2011-01-14
You have to install libtool and autopoint:
```
sudo apt-get update
sudo apt-get install libtool autopoint
```

---

### Post by lhamil64 on 2011-01-14
OK, I got past that, but when I enter:
./configure --with-buildinfo=svn/recompile
it checks for some things, and then I get the following error:
> 
checking for linux/videodev2.h... no
checking for X... no
configure: WARNING: X Windows development tools were not found.
configure: WARNING: Please install xlib-dev or xorg-x11-devel.
configure: error: Cinelerra requires X Windows.


I tried doing sudo apt-get install xlib-dev (and xorb-xll-devel) but they don't exist.

---

### Post by sisco311 on 2011-01-14
libx11-dev

---

### Post by lhamil64 on 2011-01-14
It's problem after problem with this (why can't it just install what it needs on it's own? I didn't have to go through all of this when I installed it in a VM)

It gave me a list of what's missing, but I'm not sure how to find the package names of them:
> 
libogg
libvorbis
libvorbisenc
libvorbisfile
libtheora
OpenEXR
libdv
libpng
libjpeg libraries
libjpeg headers
libtiff libraries
libtiff headers
FreeType 2
libx264 libraries
libx264 headers
libuuid libraries
libuuid headers
mjpegtools
libfftw3 libraries
libfftw3 headers
liba52 libraries
liba52 headers
libmp3lame libraries
libmp3lame headers
libsndfile libraries
libsndfile headers
libfaac libraries
libfaac headers
libfaad libraries
libfaad headers


---

### Post by sisco311 on 2011-01-14
The community documentation is old, but it may help:
[uhelp]community/amd64/Cinelerra[/uhelp]

---

### Post by lhamil64 on 2011-01-14
Thanks for all your help so far. This has been a major headache. Pretty much every command I type results in some sort of an error. 
This is the only missing mandatory component right now:
  libx264 libraries

I installed libx264-dev (which fixed libx264 headers but not libraries apparently). Do you know the package name for the libraries?

---

### Post by sisco311 on 2011-01-15
You have to compile x264 from source. For instruction see the community documentation.

---

### Post by lhamil64 on 2011-01-15
> **sisco311 said:**
> You have to compile x264 from source. For instruction see the community documentation.

I was trying that actually, but I figured out why make wouldn't work (I was in the wrong directory). Now when I try make, it gives a bunch of lines, the last one being:
make: *** [libx264.so.112] Error 1

I think it's related to not having the libx264 libraries.

---

### Post by lhamil64 on 2011-01-15
I looked through the rules/FAQ and didn't find anything about double posting or bumping, but I'm still not able to get this working. Can anyone help?

---

### Post by sisco311 on 2011-01-15
> **lhamil64 said:**
> I looked through the rules/FAQ and didn't find anything about double posting or bumping, 


It's in the [thread=885580]Forum DO'S and DON'T's[/thread].

> 
DON'T
Bump your posts too often (around once every 24 hours is recommended)

> **lhamil64 said:**
> 
but I'm still not able to get this working. Can anyone help?

Well, if you can't compile it, you can install it from the PPA repo:
[https://launchpad.net/~cinelerra-ppa/+archive/ppa/](https://launchpad.net/~cinelerra-ppa/+archive/ppa/)

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
```

---

### Post by lhamil64 on 2011-01-15
> **sisco311 said:**
> It's in the [thread=885580]Forum DO'S and DON'T's[/thread].





Well, if you can't compile it, you can install it from the PPA repo:
[https://launchpad.net/~cinelerra-ppa/+archive/ppa/](https://launchpad.net/~cinelerra-ppa/+archive/ppa/)

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
```

That worked. Thanks!

---

### Post by lhamil64 on 2011-01-15
> **sisco311 said:**
> It's in the [thread=885580]Forum DO'S and DON'T's[/thread].





Well, if you can't compile it, you can install it from the PPA repo:
[https://launchpad.net/~cinelerra-ppa/+archive/ppa/](https://launchpad.net/~cinelerra-ppa/+archive/ppa/)

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
```

That worked. Thanks!

---

### Post by lhamil64 on 2011-01-15
> **sisco311 said:**
> It's in the [thread=885580]Forum DO'S and DON'T's[/thread].





Well, if you can't compile it, you can install it from the PPA repo:
[https://launchpad.net/~cinelerra-ppa/+archive/ppa/](https://launchpad.net/~cinelerra-ppa/+archive/ppa/)

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
```

That worked. Thanks!

---

### Post by lhamil64 on 2011-01-15
> **sisco311 said:**
> It's in the [thread=885580]Forum DO'S and DON'T's[/thread].





Well, if you can't compile it, you can install it from the PPA repo:
[https://launchpad.net/~cinelerra-ppa/+archive/ppa/](https://launchpad.net/~cinelerra-ppa/+archive/ppa/)

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
```

That worked. Thanks!

---

