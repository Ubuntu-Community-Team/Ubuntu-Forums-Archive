---
title: "Install tarball from terminal, Terminal basics"
date: 2010-09-27
forum: General Help
---

### Post by winchendonsprings on 2010-09-27
I need help with my terminal basics. 

trying to install two programs (stacks for Docky, and F-Spot 0.8 ) I run into the same problem.

I extract the tarball
I cd to the folder
I run ./configure
then I cannot make, sudo make, make install.

both folder have makefile.am and makefile.in

This is what the terminal says both times 
```
 make: *** No targets specified and no makefile found.  Stop.
```Is there a dependency I don't have? What am I doing wrong?

---

### Post by lykeion on 2010-09-27
Both f-spot and docky is in the Ubuntu repositories. Simply install them with
```
sudo apt-get install docky f-spot
```
If you need the later untested versions there are PPA repositories for both (see instructions on web pages on how to install):
[https://launchpad.net/~docky-core/+archive/ppa](https://launchpad.net/~docky-core/+archive/ppa)
[https://launchpad.net/~f-spot/+archive/f-spot-ppa](https://launchpad.net/~f-spot/+archive/f-spot-ppa)

---

### Post by winchendonsprings on 2010-09-27
I have both Docky and F-spot installed. I do not have Stacks for Docky or F-spot 0.8 installed and neither are in repositories.  

basically I'm looking for a simple install .tar.bz2 from terminal lesson.

---

### Post by The Cog on 2010-09-27
You need to install build-essential from the repos before you can make and compile things.

---

### Post by lykeion on 2010-09-27
This is good compile instructions:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Also always read the README and INSTALL files in the source archive. They should give you needed dependencies to compile.

EDIT
F-Spot has compile instructions on their homepage.
Stacks for Docky - I'm not sure what this is, maybe this?
[http://www.omgubuntu.co.uk/2010/06/stacks-for-docky-looks-like-a-dream-works-like-one-too/](http://www.omgubuntu.co.uk/2010/06/stacks-for-docky-looks-like-a-dream-works-like-one-too/)

---

### Post by winchendonsprings on 2010-09-27
thanks, still having a problem. I think it's unrelated though. 

here is the terminal print outs

```
ry@ry-desktop:~$ cd stacks
ry@ry-desktop:~/stacks$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
./configure: line 2673: syntax error near unexpected token `0.35.0'
./configure: line 2673: `IT_PROG_INTLTOOL(0.35.0)'
ry@ry-desktop:~/stacks$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
./configure: line 2673: syntax error near unexpected token `0.41.0'
./configure: line 2673: `IT_PROG_INTLTOOL(0.41.0)'
ry@ry-desktop:~/stacks$ make
make: *** No targets specified and no makefile found.  Stop.
ry@ry-desktop:~/stacks$ 

```and

```
ry@ry-desktop:~/Downloads$ cd f-spot-0.8.0
ry@ry-desktop:~/Downloads/f-spot-0.8.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.35.0... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME_DOC_UTILS... yes
checking for MONO_MODULE... configure: error: Package requirements (mono >= 2.2) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

ry@ry-desktop:~/Downloads/f-spot-0.8.0$ 
```I'm going to take a wild guess that the second one needs Mono.

The first one though looks like it calls for intltool, and I have intltool 0.41.0 installed.

?

---

### Post by mc4man on 2010-09-27
For stacks you need to get from here or it will fail to build (need bzr installed
```
bzr branch lp:~docky-core/docky/stacks
```

then you'll need to run this
```
./autogen.sh
```
Reasonably likely you'll be missing some lib.'s, the configure should be fairly verbose with the exception of mono-cairo. 
forget exactly what satisfied that, start with mono-devel
(may also help with your f-spot issue

the autogen will run your first configure, after that just keep running ./configure till you're good. 

Expect to install at least 10 - 20 packages you wouldn't normally need for docky
(though wouldn't hurt to run sudo apt-get build-dep docky

---

### Post by gordintoronto on 2010-09-27
> **winchendonsprings said:**
> I have both Docky and F-spot installed. I do not have Stacks for Docky or F-spot 0.8 installed and neither are in repositories.  

basically I'm looking for a simple install .tar.bz2 from terminal lesson.

A tar is like a zip file, it's just a container for a bunch of compressed files. It is impossible to to have a simple, universal procedure for how to install from it, because it might contain anything. The install procedure could be as simple as, "copy such-and-such file to some_location," or as complex as, "install such-and-such development environment and these 40 libraries, then ...."

---

### Post by winchendonsprings on 2010-09-27
Thanks for the link. 

I ran ./configure 100 times. Needed I don't know how much stuff. I gave up. needed like 35 mono things, I gave up when I got to a few things I couldn't find in the repos. As far as Stacks, I'll just wait until it's officially released.

---

### Post by mc4man on 2010-09-27
Just for the heck went back in my synaptic history to ck. - turns out about 90 packages in 15 install groups, but i already had alot of dev's for other things, and some probably weren't needed. (chasing down the mono-cairo issue.

Probably best to wait for it to mature a bit and I did it on maverick so not sure if lucid would have package version issues 

If inclined at some point I'll make into a apt-get command, just ask..

(i also had the docky unstable ppa enabled for a couple of 'run deps'

Edit: did a quick ck. on an abandoned lucid install - out of the boatload of dep's 4 weren't available, at least one critical - gio-sharp-2.0, the maverick version/packages are not installable on lucid.
so you'd need to build that ect. - hardly worth it.

---

### Post by directhex on 2010-09-28
There are packages for both F-Spot and Docky.

If you really want to build yourself, then "apt-get build-dep docky f-spot" will install everything needed to rebuild them

---

