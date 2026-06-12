---
title: "Has anyone installed mednafen in ubuntu"
date: 2006-05-16
forum: General Help
---

### Post by ronnielsen1 on 2006-05-16
Hi. For those of you that don't know what mednafen is [http://mednafen.com/](http://mednafen.com/).
Has anyone successfully installed this. I'm getting the following errors on make. I'd appreciate any help. Thanks.

ron@desktop:~/mario/mednafen$ sudo make
Making all in intl
make[1]: Entering directory `/home/ron/mario/mednafen/intl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ron/mario/mednafen/intl'
Making all in po
make[1]: Entering directory `/home/ron/mario/mednafen/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ron/mario/mednafen/po'
Making all in src
make[1]: Entering directory `/home/ron/mario/mednafen/src'
Making all in trio
make[2]: Entering directory `/home/ron/mario/mednafen/src/trio'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ron/mario/mednafen/src/trio'
Making all in gba
make[2]: Entering directory `/home/ron/mario/mednafen/src/gba'
source='arm.cpp' object='arm.o' libtool=no \
depfile='.deps/arm.Po' tmpdepfile='.deps/arm.TPo' \
depmode=gcc3 /bin/sh ../../depcomp \
g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H  -fno-unit-at-a-time -ffast-math -I../.. -I../../include -I../../intl -I../fidlib   -I/usr/local/include   -I/usr/local/include   -I/usr/local/include    -DFIDLIB_LINUX -Wall -Winline -fomit-frame-pointer -finline-limit=6000 --param large-function-growth=800 --param inline-unit-growth=175  -I/usr/local/include/SDL -D_REENTRANT  -g -O2 -c -o arm.o `test -f 'arm.cpp' || echo './'`arm.cpp
arm.cpp: In function ‘unsigned int RunARM()’:
arm.cpp:26: internal compiler error: Bus error
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [arm.o] Error 1
make[2]: Leaving directory `/home/ron/mario/mednafen/src/gba'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/mario/mednafen/src'
make: *** [all-recursive] Error 1
ron@desktop:~/mario/mednafen$

---

### Post by pclancy on 2006-06-06
I have been able to install it successfully many times.  To be honest, I'm not sure why you're getting that error, so I'll just go over what I did to install it.  Basically what I did was:
Install all of the pakages
```

sudo apt-get install libcdio-dev
sudo apt-get install libsdl1.2-dev
sudo apt-get install libsdl-net1.2-dev
sudo apt-get install libsndfile1-dev
sudo apt-get install zlib1g-dev

```
Next, download an unpackage the mednafen source.  Then, run the configuration file:
```
./configure
```
And finally install:
```
sudo make install
```

I always forget to use sudo there, and then the make fails because it tries to create a file and the permission is denied.  I suspect that this problem was probably resolved by now, but I thought it was worth posting as a reference.

---

### Post by willneedshelp... on 2006-08-08
well i tried this and everything worked until i got the the install i am confused i type in this:

will@will-desktop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.

its probably something small and noobish for thats what i am....

---

### Post by Bragador on 2006-08-08
Could someone point me out to the FM so I can RTFM ?

As a first week linux user I can attest that I have absolutely no idea what I just installed and why and...

**What file is the damn source of mednafen !?!**

lol

weee I'm lost !

---

### Post by Sally666 on 2006-08-09
So I tried the above and it didn't work (see below)
I have 6.06 Ubuntu.  Does that make the difference?

checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

What should I do?

---

### Post by regmind on 2006-09-19
sudo apt-get install libsdl-net1.2-dev

-- I can get as far as this but ubuntu says that it can't find it - i looked on synaptic ( just in case) and it wasn't there either....  

does anyone know where this is - its preventing the make install command from completing... :(

---

### Post by regmind on 2006-09-21
I know what i needed to do now, I didn't add extra repositories where I was able to find libsdl-net1.2-dev

---

### Post by DDM on 2006-09-23
Looks like you, or anyone else who has this problem, needs to "sudo apt-get install build-essential"

---

### Post by Paerez on 2006-11-15
In edgy you can just to "sudo apt-get install mednafen". I have universe and multiverse enabled.

---

### Post by lukew on 2006-12-19
Ok,

This is as far as I got!!

I download and unzipped mednafen-0.6.5.tar.bz2

```
tar -xvpf mednafen-0.6.5.tar.bz2
```

Installed the dependencies 

```
sudo apt-get install libcdio-dev libsdl1.2-dev libsdl-net1.2-dev libsndfile1-dev zlib1g-dev
```

Installed build tools etc.

```
sudo apt-get install build-essential checkinstall

```

Created a package

```
cd mednafen
./configure
sudo checkinstall

```

The output to the terminal was 

[HTML]======================== Installation successful ==========================

Copying documentation directory...
./
./ABOUT-NLS
./AUTHORS
./COPYING
./ChangeLog
./INSTALL
./NEWS
./README
./TODO

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]:

Erasing temporary files...OK

Deleting temp dir...OK


[/HTML]

The log file produced


[HTML]dpkg-deb: parse error, in file `/var/tmp/poXbBUbpkgiOLjILYLMnQ/package/DEBIAN/control' near line 8 package `mednafen':
 newline in field name `0.6.5'

[/HTML]

Can anyone take this anyfurther?

I am running Dapper.

Thanks for your help.

Luke

---

### Post by glisteringwaters on 2007-03-05
Try this since you're an Edgy user:
go to the Ubuntu Synaptic Package Manager,
search for mednafen and add it to your system.

To start emulating your gba rom:
$ cd <rom dir>
$ mednafen <rom filename>

I'm not very sure about how to configure mednafen to manipulate multiple save/load states and speed up gameplay tho.

Anyway, I would like to thank the people who provided suggestions and instructions on how to install and use mednafen!  =D

---

### Post by lukew on 2007-04-23
> **glisteringwaters said:**
> Try this since you're an Edgy user:
go to the Ubuntu Synaptic Package Manager,
search for mednafen and add it to your system.

To start emulating your gba rom:
$ cd <rom dir>
$ mednafen <rom filename>

I'm not very sure about how to configure mednafen to manipulate multiple save/load states and speed up gameplay tho.

Anyway, I would like to thank the people who provided suggestions and instructions on how to install and use mednafen!  =D

I would just like to point out that when the posts was written this was not in the repos. Trust me that is the first place i would look!!

---

### Post by glisteringwaters on 2007-04-30
Okay, since it has been a long time since I posted that reply, I am not sure if the Synaptic Package Manager really did have mednafen in the repository.

Perhaps I used the command line sudo apt-get but I am not so sure.

Anyway since mednafen shows up when I search the repository now (main universe multiverse) - I'll assume that installing Mednafen from the Synaptic Package Manager interface should resolve all dependencies and get the emulator set up properly...

---

### Post by lukew on 2007-05-01
> **glisteringwaters said:**
> Okay, since it has been a long time since I posted that reply, I am not sure if the Synaptic Package Manager really did have mednafen in the repository.

Perhaps I used the command line sudo apt-get but I am not so sure.

Anyway since mednafen shows up when I search the repository now (main universe multiverse) - I'll assume that installing Mednafen from the Synaptic Package Manager interface should resolve all dependencies and get the emulator set up properly...

Your reply was 5 weeks ago; the previous entry was over 5 months ago!

BTW yes it is in the feisty universe repos.

---

### Post by glisteringwaters on 2007-05-08
@lukew: I was just trying to help!

---

### Post by earobinson on 2007-05-08
worked for me out of the box :)

---

