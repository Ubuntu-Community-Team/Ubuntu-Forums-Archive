---
title: "vis5d+ on Ubuntu Karmic"
date: 2010-06-18
forum: General Help
---

### Post by spacefizzicist on 2010-06-18
Dear all,

I have downloaded the visualization package vis5d+ and trying to install on Ubuntu Karmic. After untarring I do:
me@mysystem:~/vis5d+-1.3.0-beta$ ./configure --prefix=/home/vis5d+/ --with-mesa=/usr/lib --with-netcdf=/usr/lib --enable-threads --with-memory=0  --with-libgtk 

and it craps out saying:

****************************************************
You need to install a 3D graphics library, preferably
the free OpenGL replacement, Mesa.  You can download
Mesa from the Mesa home page:
  	    [http://www.mesa3d.org/](http://www.mesa3d.org/)
and install it by running:
       ./configure && make && su -c 'make install'
in the Mesa directory.
You may also need to run /sbin/ldconfig as root
to update the system after installing Mesa.
(First, add '/usr/local/lib' to /etc/ld.so.conf if
you installed Mesa under /usr/local, the default.)
****************************************************
configure: error: couldn't find 3D graphics library

But I made symlinks in /usr/lib:

root@mysystem:~# ln -s libGL.so libMesaGL.so 
and
root@mysystem:~# ln -s libGLU.so libMesaGLU.so 

But still no luck. I do have 
libglu1-mesa - The OpenGL utility library (GLU)
libglu1-mesa-dev - The OpenGL utility library -- development files
mesa-common-dev 
etc. installed. I am attaching the config file for vis5d+ and also the config.log file.
If anyone has walked this way before, can you pls let me know what is going wrong here?

my system is: Ubuntu Karmic 9.04, with kernel 2.6.31-22-generic and gcc 4.4.1

Many thanks in advance for your time and any help.

~R

---

### Post by gzarkadas on 2010-06-18
From what I figured from your attached files: the --with-mesa is a on/off toggle option; you should not append =/usr/lib to it. Also --with-netcdf=/usr/lib is not correct; you must specify the complete path to the library file there, not just the containing folder. Try to not use it and let the autofind logic of configure to do it. In addition I didn't find --with-libgtk in the help text; maybe you mean --enable-gtk?

Try to run configure with the options below and see if the problem is solved:
```

./configure --prefix=/home/vis5d+/ --with-mesa --enable-threads --enable-gtk 

```I would also suggest to not use --prefix=/home/vis5d+/ and let the default (/usr/local) which is the recommended place for locally installed software; /home is for human users' data and it will help you in the long run to keep things well-separated. So, consider using just this:

```

./configure --with-mesa --enable-threads --enable-gtk 

```

---

### Post by spacefizzicist on 2010-06-18
Thank you for your reply. I have already tried it out, but no luck! I was wondering why the Mesa lib error would come? If I don't explicitly provide the path then this happens:
> checking for X... no
checking for glBegin in -lMesaGL... no
checking for glBegin in -lGL... no
couldn't find OpenGL libraries!
configure: error: couldn't find Mesa library
Hence, I put symlinks in the /usr/lib thinking it is looking for libMesaGL etc. The documentation is here:
[http://vis5d.sourceforge.net/doc/ch02sec2.html](http://vis5d.sourceforge.net/doc/ch02sec2.html)
and the code is here: [http://sourceforge.net/projects/vis5d/files/](http://sourceforge.net/projects/vis5d/files/)
If any of you guys have time, I'd appreciate it if you can check if you can get past configure on your Karmic!
Thanks much in advance,
~R

---

### Post by gzarkadas on 2010-06-18
Try to omit the `--with-mesa' option; recent versions of Mesa install libs with names following OpenGL.

---

### Post by spacefizzicist on 2010-06-18
Well, no luck! Seems from the release date (2002 April) that its been quite a while since this s/w has been updated - so I don't know if there is any issues with libMesaGL and libGL. Symlinks didn't help and configuring without these options didn't work either. I am getting the same error:

checking for glBegin in -lGL... no
checking for glBegin in -lMesaGL... no
couldn't find OpenGL libraries!
checking for bgnqstrip in -lgl_s... no
****************************************************
You need to install a 3D graphics library, preferably
the free OpenGL replacement, Mesa.  You can download
Mesa from the Mesa home page:
  	    [http://www.mesa3d.org/](http://www.mesa3d.org/)
and install it by running:
       ./configure && make && su -c 'make install'
in the Mesa directory.
You may also need to run /sbin/ldconfig as root
to update the system after installing Mesa.
(First, add '/usr/local/lib' to /etc/ld.so.conf if
you installed Mesa under /usr/local, the default.)
****************************************************
configure: error: couldn't find 3D graphics library
------------
Thanks anyways. I appreciate your time and help.
~R

---

### Post by gzarkadas on 2010-06-19
Before giving up, try to open the Synaptic Package Manager (from menu System|Administration), select `All' from the list at the left, type `mesa' in the search box and hit enter. It will output a list of openGL mesa libraries. See if any library is installed and/or try to install some. A few possible packages to tryout:

mesa-common-dev
libgl1-mesa-dev
libgl1-mesa-swx11-dev

Then rerun configure.

---

