---
title: "Where do I get lib64 from?"
date: 2012-03-25
forum: General Help
---

### Post by 7o7YlUcb on 2012-03-25
Hi, I'm trying to compile some software. I'm following the instruction in the INSTALL file...
When I run...
CFLAGS="-g -Wall" ./configure --enable-64bit --with-libs=/usr/lib64 
It comes back with the error...
configure: error: *** Library directory /usr/lib64 does not exist.

I'm guessing this is some general thing rather that something specific to the software I'm trying to install. Any ideas what this means or where I get it?

(In case its relevant I'm trying to install grass6.4.2 in 64-bit mode. [http://grass.osgeo.org/grass64/source/grass-6.4.2.tar.gz](http://grass.osgeo.org/grass64/source/grass-6.4.2.tar.gz))
Thanks.

---

### Post by kc1di on 2012-03-25
Hi grass 6.4.1 is available in the repository so lib64 should be there as a dependency. Is there a lot of difference between 6.4.1 and 6.4.2?

Also the grass web page says the have an Ubuntu PPA which means you can install there repository and install the program with all the needed dependencies so you should not need to configure it yourself.  

here is their ppa page 
[https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable]("https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable")

if you need help with how to activate the PPA repository let us know we can walk you through it.

---

### Post by 7o7YlUcb on 2012-03-25
Thanks Dave,

I need to use Grass 6.4.2 as v.voronoi has a bug in 6.4.1
I have confirmed this by running 6.4.1 and 6.4.2 on windows
However I cant use grass on windows for the full data set as I need access to more than the 2GB (Windows grass only seems to be readably available in 32-bit).

The GRASS web pages says that 6.4.2 binaries are available for Ubuntu. But as far as I can tell this is not the case. The link you listed says the package includes 6.4.1-2. Not sure what this means. But when I install grass from this repository it installs 6.4.1.

I found generic (not ubuntu specific) 64-bit binaries for version 6.4.3 but it came up with errors when I tried to install it. So at this point I though of going down the compile option. Thinking this was a bad idea though.

Anyway I did as you suggested and installed 6.4.1 again. However there is no directory: /usr/lib64
?

There is a folder /lib64 though - it contains one link file to /lib/x86_64-linux-gnu/ld-2.13.so
I tried changing the CFLAGS command to use this file but then it jsut came up with an error saying it couldnt locate "lex". So I'm guessing this is not the same thing

---

### Post by Pand5461 on 2012-03-25
> **kc1di said:**
> 
Also the grass web page says the have an Ubuntu PPA which means you can install there repository and install the program with all the needed dependencies so you should not need to configure it yourself.  


I agree, it's better to use PPA when possible.

If you still want to compile it from source, the default library directory is /usr/lib not /usr/lib64.

If you're going to compile more software, I'd recommend you get some notion of how to use compiler/linker flags.

---

### Post by kc1di on 2012-03-25
just so you will know the /usr/lib64 is not the file it's looking for it's looking for lib64 , but when I do a search for in in synaptic there are several so without down loading the source code and looking at the readme files I'm not sure exactly which lib64 file it's asking for i'm not sure.

the problem is that there may be more dependencies you'll have to chase down also. but it can be done sometimes it will take a bit of detective work to find out what programs supply what files though.
Good Luck with it. you will have to have all dependencies installed before ./configure will complete without errors.

Dave

you can add there Personal repository by in a terminal using the following command <sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable> (Without the brackets)  and see if it pulls 6.4.2
you will a have to do sudo apt-get update after then search for your program

---

### Post by Yellow Pasque on 2012-03-25
> --with-libs=/usr/lib64
Either use /usr/lib or make a /usr/lib64 symlink pointing to /usr/lib

> the problem is that there may be more dependencies you'll have to chase down
apt-get build-dep usually gets most (if not all) required dependencies:
```
sudo apt-get build-dep grass
```

---

### Post by 7o7YlUcb on 2012-03-25
Thanks Dave, Temüjin,

I tried ...
CFLAGS="-g -Wall" ./configure --enable-64bit --with-libs=/usr/lib
..but then get ...
configure: error: *** Unable to locate lex.

Running 'locate' I get this...
```
/lib64
/lib64/ld-linux-x86-64.so.2
/usr/src/linux-headers-3.0.0-12/arch/sh/lib64
/usr/src/linux-headers-3.0.0-12/arch/sh/lib64/Makefile
/usr/src/linux-headers-3.0.0-16/arch/sh/lib64
/usr/src/linux-headers-3.0.0-16/arch/sh/lib64/Makefile
```I tried all of these directories but get the same error.

What I dont understand is why it would need a missing dependancy? As suggested: I installed 6.4.1, check it runs and check it is a 64-bit application. Then without uninstalling it, try to compile 6.4.2. You would think there wouldnt be much difference so it wouldn't need extra stuff like lib64 which sounds kind of fundamental.

> you can add there Personal repository by in a terminal using the  following command <sudo add-apt-repository  ppa:ubuntugis/ubuntugis-unstable> (Without the brackets)  and see if  it pulls 6.4.2
you will a have to do sudo apt-get update after then search for your program     Do you mean to add the repository, install GRASS it and run it? This is what I did and GRASS says it is 6.4.1
The GRASS website implies that 6.4.2 is available as a binary for Ubuntu but as far as I can tell it is not. Ie 6.4.2 is not available in a PPA.
I do this...

sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update
sudo apt-get install grass
grass  

..and the GUI that pops up says it is grass 6.4.1.

---

### Post by Yellow Pasque on 2012-03-25
```
sudo apt-get install flex
```
Then, try build again.

---

### Post by kc1di on 2012-03-25
> **RevRhubar said:**
> 

Do you mean to add the repository, install GRASS it and run it? This is what I did and GRASS says it is 6.4.1
The GRASS website implies that 6.4.2 is available as a binary for Ubuntu but as far as I can tell it is not. Ie 6.4.2 is not available in a PPA.
I do this...

sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update
sudo apt-get install grass
grass  

..and the GUI that pops up says it is grass 6.4.1.

Well I was only going by the web site Don't have installed myslef but they sure make it sound as if it's available in their unstable PPA.  Oh well guess if you want it you'll have to figure what dependencies are missing and install them one at at time. the problem is that they mostlikely changed the version # on many of the deps also so the old ones don't look like the right ones for 6.4.2  Run into this with claws mail also every time they update to a newer version you have to rebuild all the plugins also even though they haven't really changed.

Hope you get it worked out.

---

### Post by 7o7YlUcb on 2012-03-26
I tried 
sudo apt-get install flex

but didnt have success.

I hadnt appreciated how tricky it could be to compile things on Linux. I think what I'll do is temporarily install another linux distro that does have 6.4.2 available. I think this wlll be quicker in the long run.

Anyway, thanks for all your help and suggestions

---

### Post by Yellow Pasque on 2012-03-26
flex is one of the build dependencies, and it should have been installed when you ran:
```
sudo apt-get build-dep grass
```
I assumed you ran that, but apparently, you didn't.... (silly me).

For reference, here's the list of stuff build-dep grass should install:
```
Build-depends: flex, bison,libreadline-dev | libreadline6-dev, libncurses5-dev, lesstif2-dev, debhelper (>= 7), 
 libtiff4-dev, tcl-dev (>= 8.5), tk-dev (>= 8.5), libfftw3-dev, libxmu-dev, libglu1-mesa-dev | libglu1-xorg-dev, 
 libfreetype6-dev, autoconf2.13, autotools-dev, libgdal1-dev (>= 1.5.0), libproj-dev, proj-bin, libjpeg-dev, 
 libpng12-dev, libpq-dev, unixodbc-dev, doxygen, fakeroot, libmysqlclient-dev, graphviz, libsqlite3-dev, python-wxgtk2.8,
 libcairo2-dev, libwxgtk2.8-dev, python-dev (>= 2.5), swig
```

---

### Post by Pand5461 on 2012-03-26
> **RevRhubar said:**
> 
I hadnt appreciated how tricky it could be to compile things on Linux.
It's easy if you try :) You might be interested in  [this howto]("http://www.howtogeek.com/106526/how-to-resolve-dependencies-while-compiling-software-on-ubuntu/").

---

