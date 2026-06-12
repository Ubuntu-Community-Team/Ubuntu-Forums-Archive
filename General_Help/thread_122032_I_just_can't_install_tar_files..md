---
title: "I just can't install tar files."
date: 2006-01-26
forum: General Help
---

### Post by Sewage on 2006-01-26
Can some one give me a step by step on how to do this, I've followed a few but always get "no make file" errors and it's getting sad. ):

---

### Post by MartinG on 2006-01-26
First point, have you installed the package "build-essential"?

Second, have you installed any headers/development files needed (check the README in the Tar package)?

Third, I presume you've unpacked the tar package and entered the directory.

(Sorry if the questions are too basic, but you haven't given much information)

Once the above are all done it is a matter of the following:[INDENT]./configure
make
sudo make install[/INDENT]Actually I prefer to install the package Checkinstall, and replace the last line with[INDENT]sudo checkinstall[/INDENT]This creates a deb package, and ensures easy removal at a later date.

---

### Post by Sewage on 2006-01-26
No, I'm sorry for my lack of information.

Let me check all the things you listed and try again, if there is another error I will list it completely with the steps that brought me there.

---

### Post by Elrond on 2006-01-26
Well, I also have a problem with tar files. I was wondering how do I unpack .tar.bz2 becouse I need it for skype. Yes I know I already have .deb file but I'm running amd64 so that doesn't work for me. 

Plz tell me what to do.[-o<

---

### Post by Sewage on 2006-01-26
Okay, here our the steps I took leading up to the error.

> brad@towardzero:~$ tar xvjf revelation-0.4.6.tar.bz2
revelation-0.4.6/
revelation-0.4.6/src/
revelation-0.4.6/src/lib/
revelation-0.4.6/src/lib/data.py
revelation-0.4.6/src/lib/io.py
revelation-0.4.6/src/lib/ui.py
revelation-0.4.6/src/lib/datahandler/
revelation-0.4.6/src/lib/datahandler/xhtml.py
revelation-0.4.6/src/lib/datahandler/pwsafe.py
revelation-0.4.6/src/lib/datahandler/text.py
revelation-0.4.6/src/lib/datahandler/fpm.py
revelation-0.4.6/src/lib/datahandler/Makefile.am
revelation-0.4.6/src/lib/datahandler/Makefile.in
revelation-0.4.6/src/lib/datahandler/rvl.py
revelation-0.4.6/src/lib/datahandler/netrc.py
revelation-0.4.6/src/lib/datahandler/base.py
revelation-0.4.6/src/lib/datahandler/gpass.py
revelation-0.4.6/src/lib/datahandler/__init__.py
revelation-0.4.6/src/lib/config.py.in
revelation-0.4.6/src/lib/dialog.py
revelation-0.4.6/src/lib/Makefile.am
revelation-0.4.6/src/lib/Makefile.in
revelation-0.4.6/src/lib/entry.py
revelation-0.4.6/src/lib/util.py
revelation-0.4.6/src/lib/__init__.py
revelation-0.4.6/src/wrap/
revelation-0.4.6/src/wrap/gnomemisc/
revelation-0.4.6/src/wrap/gnomemisc/gnomemiscmodule.c
revelation-0.4.6/src/wrap/gnomemisc/gnomemisc.defs
revelation-0.4.6/src/wrap/gnomemisc/gnomemisc.override
revelation-0.4.6/src/wrap/gnomemisc/Makefile.am
revelation-0.4.6/src/wrap/gnomemisc/Makefile.in
revelation-0.4.6/src/wrap/crack/
revelation-0.4.6/src/wrap/crack/Makefile.am
revelation-0.4.6/src/wrap/crack/Makefile.in
revelation-0.4.6/src/wrap/crack/crack.c.in
revelation-0.4.6/src/wrap/Makefile.am
revelation-0.4.6/src/wrap/Makefile.in
revelation-0.4.6/src/revelation.in
revelation-0.4.6/src/Makefile.am
revelation-0.4.6/src/Makefile.in
revelation-0.4.6/src/revelation-applet.in
revelation-0.4.6/NEWS
revelation-0.4.6/TODO
revelation-0.4.6/data/
revelation-0.4.6/data/ui/
revelation-0.4.6/data/ui/popup-tree.xml
revelation-0.4.6/data/ui/toolbar.xml
revelation-0.4.6/data/ui/actions.xml
revelation-0.4.6/data/ui/menubar.xml
revelation-0.4.6/data/ui/Makefile.am
revelation-0.4.6/data/ui/Makefile.in
revelation-0.4.6/data/mime/
revelation-0.4.6/data/mime/Makefile.am
revelation-0.4.6/data/mime/Makefile.in
revelation-0.4.6/data/mime/revelation.desktop
revelation-0.4.6/data/mime/revelation.xml
revelation-0.4.6/data/gconf/
revelation-0.4.6/data/gconf/revelation-applet.schemas
revelation-0.4.6/data/gconf/Makefile.am
revelation-0.4.6/data/gconf/Makefile.in
revelation-0.4.6/data/gconf/revelation.schemas
revelation-0.4.6/data/icons/
revelation-0.4.6/data/icons/16x16/
revelation-0.4.6/data/icons/16x16/Makefile.am
revelation-0.4.6/data/icons/16x16/Makefile.in
revelation-0.4.6/data/icons/16x16/revelation.png
revelation-0.4.6/data/icons/24x24/
revelation-0.4.6/data/icons/24x24/revelation-locked.png
revelation-0.4.6/data/icons/24x24/Makefile.am
revelation-0.4.6/data/icons/24x24/Makefile.in
revelation-0.4.6/data/icons/24x24/revelation.png
revelation-0.4.6/data/icons/32x32/
revelation-0.4.6/data/icons/32x32/revelation-locked.png
revelation-0.4.6/data/icons/32x32/Makefile.am
revelation-0.4.6/data/icons/32x32/Makefile.in
revelation-0.4.6/data/icons/32x32/revelation.png
revelation-0.4.6/data/icons/48x48/
revelation-0.4.6/data/icons/48x48/gnome-mime-application-x-revelation.png
revelation-0.4.6/data/icons/48x48/revelation-locked.png
revelation-0.4.6/data/icons/48x48/Makefile.am
revelation-0.4.6/data/icons/48x48/Makefile.in
revelation-0.4.6/data/icons/48x48/revelation.png
revelation-0.4.6/data/icons/scalable/
revelation-0.4.6/data/icons/scalable/revelation-fallback-folder.svg
revelation-0.4.6/data/icons/scalable/Makefile.am
revelation-0.4.6/data/icons/scalable/Makefile.in
revelation-0.4.6/data/icons/scalable/revelation-fallback-folder-open.svg
revelation-0.4.6/data/icons/Makefile.am
revelation-0.4.6/data/icons/Makefile.in
revelation-0.4.6/data/bonobo/
revelation-0.4.6/data/bonobo/GNOME_RevelationApplet.server.in
revelation-0.4.6/data/bonobo/Makefile.am
revelation-0.4.6/data/bonobo/Makefile.in
revelation-0.4.6/data/Makefile.am
revelation-0.4.6/data/Makefile.in
revelation-0.4.6/data/cracklib/
revelation-0.4.6/data/cracklib/Makefile.am
revelation-0.4.6/data/cracklib/Makefile.in
revelation-0.4.6/data/cracklib/pwdict
revelation-0.4.6/depcomp
revelation-0.4.6/aclocal.m4
revelation-0.4.6/README
revelation-0.4.6/configure
revelation-0.4.6/configure.ac
revelation-0.4.6/install-sh
revelation-0.4.6/autogen.sh
revelation-0.4.6/missing
revelation-0.4.6/mkinstalldirs
revelation-0.4.6/Makefile.am
revelation-0.4.6/Makefile.in
revelation-0.4.6/acinclude.m4
revelation-0.4.6/AUTHORS
revelation-0.4.6/INSTALL
revelation-0.4.6/ChangeLog
revelation-0.4.6/COPYING
revelation-0.4.6/py-compile
brad@towardzero:~$ cd revelation-0.4.6
brad@towardzero:~/revelation-0.4.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking Python include path... /usr/include/python2.4
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.3.90) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PYGTK_CFLAGS and PYGTK_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
brad@towardzero:~/revelation-0.4.6$ sudo make
make: *** No targets specified and no makefile found.  Stop.
brad@towardzero:~/revelation-0.4.6$


---

### Post by MartinG on 2006-01-26
[QUOTE=Elrond]Well, I also have a problem with tar files. I was wondering how do I unpack .tar.bz2 becouse I need it for skype. Yes I know I already have .deb file but I'm running amd64 so that doesn't work for me. 

Plz tell me what to do.[-o<[/QUOTE]Try
[INDENT]tar -jxvf file.tar.bz2[/INDENT]Mind you, a right click in Nautilus/Konqueror might offer to extract it using Fileroller/Ark.  Or you could start one of the se programs and "feed" it the file.

---

### Post by aysiu on 2006-01-26
Are you installing Revelation from source because you want the brand-spanking-new version of it, or because you don't realize there's an easier way to install it?

If you don't realize there's an easier way, trash the tarball, see the first link of my signature to get the Universe repositories, then ```
sudo apt-get update
sudo apt-get install revelation
``` That's it.

---

### Post by Sewage on 2006-01-26
I don't want an easy way out, though I thank you for offering it.

I would really like to know how to do this.

---

### Post by GeneralZod on 2006-01-26
[QUOTE=Sewage]I don't want an easy way out, though I thank you for offering it.

I would really like to know how to do this.[/QUOTE]

"make" failed because your "./configure" failed (./configure must complete successfully before you go on to the "make" step) - the error returned was:

```

checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.3.90) were not met.

```

indicating that either pygtk-2.0 or the corresponding dev files were missing.

Searching through synaptic for "pygtk" gives a whole bunch of options; installing python-gtk2 and python-gtk2-dev seems like the best bet.  Do this via synaptic, then run ./configure again, pay attention to any files or libraries it requires and install them via Synaptic.  Repeat until your "./configure" completes successfully.

Edit: VVV

:)

---

### Post by MartinG on 2006-01-26
Thankyou, GeneralZod, you beat me to the punch :)

---

### Post by Sewage on 2006-01-26
Okay, I installed everything ./configure needed and it all went though.

I performed a sudo make but towards the end was faced with these erros.

> make[3]: Leaving directory `/home/brad/revelation-0.4.6/data/icons/16x16'
Making all in 24x24
make[3]: Entering directory `/home/brad/revelation-0.4.6/data/icons/24x24'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/brad/revelation-0.4.6/data/icons/24x24'
Making all in 32x32
make[3]: Entering directory `/home/brad/revelation-0.4.6/data/icons/32x32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/brad/revelation-0.4.6/data/icons/32x32'
Making all in 48x48
make[3]: Entering directory `/home/brad/revelation-0.4.6/data/icons/48x48'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/brad/revelation-0.4.6/data/icons/48x48'
Making all in scalable
make[3]: Entering directory `/home/brad/revelation-0.4.6/data/icons/scalable'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/brad/revelation-0.4.6/data/icons/scalable'
make[3]: Entering directory `/home/brad/revelation-0.4.6/data/icons'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/brad/revelation-0.4.6/data/icons'
make[2]: Leaving directory `/home/brad/revelation-0.4.6/data/icons'
Making all in mime
make[2]: Entering directory `/home/brad/revelation-0.4.6/data/mime'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/brad/revelation-0.4.6/data/mime'
Making all in ui
make[2]: Entering directory `/home/brad/revelation-0.4.6/data/ui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/brad/revelation-0.4.6/data/ui'
make[2]: Entering directory `/home/brad/revelation-0.4.6/data'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/brad/revelation-0.4.6/data'
make[1]: Leaving directory `/home/brad/revelation-0.4.6/data'
Making all in src
make[1]: Entering directory `/home/brad/revelation-0.4.6/src'
Making all in lib
make[2]: Entering directory `/home/brad/revelation-0.4.6/src/lib'
Making all in datahandler
make[3]: Entering directory `/home/brad/revelation-0.4.6/src/lib/datahandler'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/brad/revelation-0.4.6/src/lib/datahandler'
make[3]: Entering directory `/home/brad/revelation-0.4.6/src/lib'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/brad/revelation-0.4.6/src/lib'
make[2]: Leaving directory `/home/brad/revelation-0.4.6/src/lib'
Making all in wrap
make[2]: Entering directory `/home/brad/revelation-0.4.6/src/wrap'
Making all in crack
make[3]: Entering directory `/home/brad/revelation-0.4.6/src/wrap/crack'
sed \
-e "s|\@CRACK_DICTPATH\@|/var/cache/cracklib/cracklib_dict|" \
        crack.c.in >crack.c
gcc -pthread -fno-strict-aliasing -fPIC -I/usr/include/python2.4 -c crack.c -o crack.o
crack.c:21:20: error: Python.h: No such file or directory
crack.c:43: error: syntax error before ‘*’ token
crack.c:43: error: syntax error before ‘*’ token
crack.c: In function ‘crack_FascistCheck’:
crack.c:56: error: ‘args’ undeclared (first use in this function)
crack.c:56: error: (Each undeclared identifier is reported only once
crack.c:56: error: for each function it appears in.)
crack.c:63: error: ‘PyExc_IOError’ undeclared (first use in this function)
crack.c:70: warning: assignment discards qualifiers from pointer target type
crack.c:71: error: ‘PyExc_ValueError’ undeclared (first use in this function)
crack.c:75: warning: return makes pointer from integer without a cast
crack.c: At top level:
crack.c:78: error: syntax error before ‘crack_methods’
crack.c:79: warning: braces around scalar initializer
crack.c:79: warning: (near initialization for ‘crack_methods[0]’)
crack.c:79: warning: initialization makes integer from pointer without a cast
crack.c:79: warning: excess elements in scalar initializer
crack.c:79: warning: (near initialization for ‘crack_methods[0]’)
crack.c:79: error: ‘METH_VARARGS’ undeclared here (not in a function)
crack.c:79: warning: excess elements in scalar initializer
crack.c:79: warning: (near initialization for ‘crack_methods[0]’)
crack.c:79: warning: excess elements in scalar initializer
crack.c:79: warning: (near initialization for ‘crack_methods[0]’)
crack.c:80: warning: braces around scalar initializer
crack.c:80: warning: (near initialization for ‘crack_methods[1]’)
crack.c:80: warning: initialization makes integer from pointer without a cast
crack.c:81: warning: data definition has no type or storage class
crack.c:90: error: syntax error before ‘initcrack’
crack.c: In function ‘initcrack’:
crack.c:92: error: ‘PyObject’ undeclared (first use in this function)
crack.c:92: error: ‘m’ undeclared (first use in this function)
crack.c:92: error: ‘d’ undeclared (first use in this function)
crack.c:92: error: ‘dictpath’ undeclared (first use in this function)
make[3]: *** [crack.o] Error 1
make[3]: Leaving directory `/home/brad/revelation-0.4.6/src/wrap/crack'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/brad/revelation-0.4.6/src/wrap'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brad/revelation-0.4.6/src'
make: *** [all-recursive] Error 1


---

### Post by GeneralZod on 2006-01-26
Looks like whoever wrote the configure script missed out a dependency - you did everything right, so they're to blame :)

The compiler is missing python.h - at a guess, I'd suggest installing 

python-dev

---

### Post by codejunkie on 2006-01-26
[QUOTE=Sewage]Can some one give me a step by step on how to do this, I've followed a few but always get "no make file" errors and it's getting sad. ):[/QUOTE]
it varies between packages to get you started 
open a terminal and copy and paste this in there
```

sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 libstdc++5 checkinstall
```
this will install the basic compilers and things to help you build apps but some packages require you to install other development packages i can't tell you which ones because every package is different but i'll show you how to find out. now extract the tar files, open a terminal, and cd into the directory you extracted. now follow these steps
```
./configure --prefix=/usr
```
this will configure the package if you get any errors here this is where the other development packages i mentioned come into play it will tell you what your missing you then need to open synaptic and find that package/packages your missing and install them and re-run 
```
./configure --prefix=/usr
```
with some apps this might happen more than once you just have to repeat the steps until you have the needed packages once ./configure has finished it usualy will say GOOD start MAKE
-----------------------------------------------------------------------------------------------------------------
this is where debian/ubuntu is great if the package your trying to install is in the repo and your just wanting to install a newer version you can just do this step to avoid tracking down packages 
```
sudo apt-get build-dep nameofpackage
```
this will download and install all dependencies and then all you have to do is run ```
./configure --prefix=/usr
```
-----------------------------------------------------------------------------------------------------------------
you can also skip tracking down most package dependencies by doing this it takes up a little more disk space around 250-300mb because it installs all of kde and gnome development packages but i thought id add it because it saves time.
```
sudo apt-get install gnome-dev* kde-dev*
```
-----------------------------------------------------------------------------------------------------------------
after ./configure --prefix=/usr finishes with no errors start make with
```
make
```
when make finishes look at just the end of the file if you see errors at the end of the file don't install. errors in make usualy happen with unstable development packages you'll have to either download a stable version or wait until the devolpement version matures a bit.
-----------------------------------------------------------------------------------------------------------------
now installing if all goes well with ./configure and make 
you have a couple of options here checkinstall and make install with checkinstall it creates a .deb package that can be copied over to disk to install again later and can be uninstalled easily through synaptic this is only good for small packages that dont overwrite system files if your installing a bigger package such as gimp that overwrites some system files checkinstall will sometimes error out and you'll have to use make install.
to run checkinstall use
```
sudo checkinstall
```you will be prompted for some info change what you want and press enter when it's finished it will let you know and where it created the .deb package it's usually in the program's source directory now you can move the .deb package and delete the source dir.
to run make install use 
```
sudo make install
```this will install the files and let you know when it's finished if you use make install when your done **do not delete the programs source folder** you will need it if you ever wan't to uninstall the app if you delete it you have to manually track down the files installed and remove them which kinda sucks
if you want to uninstall the app open a terminal cd to the programs source dir and run ```
sudo make uninstall
``` 
i know this is a long and drawn out guide sorry for that but i hope it helps.

---

### Post by Sewage on 2006-01-26
No, it was very helpful codejunkie. Thank you for spending the time writing it~

---

### Post by MartinG on 2006-01-26
make doesn't need to be run as sudo -- but I don't think that's the problem.

I must admit, if this happens to me I give up at this point, in the belief that this is a problem of the program rather than anything I can sort out, but others may know better.

It looks like a file Python.h is missing.  Either it's not been installed, or perhaps the make script is looking for Python.h when python.h is on the system.  Why not search for python.h, and if it is there create a symlink to it called Python.h, and try again?

---

### Post by Sewage on 2006-01-26
Hahaha~ I did it! I installed my first .tar~ how fantastic! I got a few more errors afterwards but did my best to get past them. It's all up and running now. 

I've copied all of your helpful advice to a text document to help me later if needed. :D Thank you guys so much, I hope one day I can return the favor by helping here too.

---

