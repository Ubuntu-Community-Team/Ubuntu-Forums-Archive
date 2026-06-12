---
title: "How to upgrade tomboy?"
date: 2011-04-09
forum: General Help
---

### Post by _nikolaos on 2011-04-09
There is a new version of Tomboy (1.6.0) and I want to upgrade my current version 1.2.2. However, I can't figure out how.

1. There is no installation help for Linux users in Tomboy website;
2. Console **sudo apt-get install tomboy** returns that I am already at the newest version;
3. The same way with Synaptic Package Manager and Ubuntu Software Center;
4. Last idea, I manually downloaded the tarball file, extracted it on the desktop, and typed in the terminal the following:
```
cd ~/Desktop/tomboy-1.6.0/
./configure
```

for each error that the check returned, I installed (sudo apt-get install) whatever missing: it was intltool and mono-gmcs.

```
sudo apt-get install intltool
sudo apt-get install mono-gmcs
```

I ran **./configure** for a third time, this is what I got:
```
~/Desktop/tomboy-1.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking gnome-doc-utils >= 0.17.3... yes
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.35... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gmcs... /usr/bin/gmcs
checking for MONO... no
configure: error: Package requirements (mono >= 1.9.1) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

That time I couldn't make out what is all this about, as I typed **mono --version** and returned a newer version than what had been claimed to be.
```
~/Desktop/tomboy-1.6.0$ mono --version
Mono JIT compiler version 2.4.4 (Debian 2.4.4~svn151842-1ubuntu4)
Copyright (C) 2002-2010 Novell, Inc and Contributors. www.mono-project.com
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  x86
	Disabled:      none

```

I guessed that this might be some kind of warning, so I dared to start **make**, but it did not work:
```
~/Desktop/tomboy-1.6.0$ make
make: *** No targets specified and no makefile found.  Stop.
~/Desktop/tomboy-1.6.0$ make install
make: *** No rule to make target `install'.  Stop.

```

I am puzzled, I know there are things that I don't know, but I ask for your help either to guide me upgrade tomboy at last, or to help me understand all about those things in the process I followed.

Thanks.

EDIT: Just one more, is this upgrade enough to get the tomboy applet for my AWN dock available to put?

---

### Post by tgm4883 on 2011-04-09
> **_nikolaos said:**
> There is a new version of Tomboy (1.6.0) and I want to upgrade my current version 1.2.2. However, I can't figure out how.

1. There is no installation help for Linux users in Tomboy website;
2. Console **sudo apt-get install tomboy** returns that I am already at the newest version;
3. The same way with Synaptic Package Manager and Ubuntu Software Center;
4. Last idea, I manually downloaded the tarball file, extracted it on the desktop, and typed in the terminal the following:
```
cd ~/Desktop/tomboy-1.6.0/
./configure
```

for each error that the check returned, I installed (sudo apt-get install) whatever missing: it was intltool and mono-gmcs.

```
sudo apt-get install intltool
sudo apt-get install mono-gmcs
```

I ran **./configure** for a third time, this is what I got:
```
~/Desktop/tomboy-1.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking gnome-doc-utils >= 0.17.3... yes
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.35... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gmcs... /usr/bin/gmcs
checking for MONO... no
configure: error: Package requirements (mono >= 1.9.1) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

That time I couldn't make out what is all this about, as I typed **mono --version** and returned a newer version than what had been claimed to be.
```
~/Desktop/tomboy-1.6.0$ mono --version
Mono JIT compiler version 2.4.4 (Debian 2.4.4~svn151842-1ubuntu4)
Copyright (C) 2002-2010 Novell, Inc and Contributors. www.mono-project.com
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  x86
	Disabled:      none

```

I guessed that this might be some kind of warning, so I dared to start **make**, but it did not work:
```
~/Desktop/tomboy-1.6.0$ make
make: *** No targets specified and no makefile found.  Stop.
~/Desktop/tomboy-1.6.0$ make install
make: *** No rule to make target `install'.  Stop.

```

I am puzzled, I know there are things that I don't know, but I ask for your help either to guide me upgrade tomboy at last, or to help me understand all about those things in the process I followed.

Thanks.


I'd probably just use the tomboy packagers PPA, but it doesn't look like they have 1.6 yet

[https://launchpad.net/~tomboy-packagers/+archive/stable](https://launchpad.net/~tomboy-packagers/+archive/stable)

> **_nikolaos said:**
> 
EDIT: Just one more, is this upgrade enough to get the tomboy applet for my AWN dock available to put?

No. AWN applets are in AWN packages. According to this page

[http://wiki.awn-project.org/Tomboy_Applet](http://wiki.awn-project.org/Tomboy_Applet)

it is in AWN Extras since version 0.3.2

---

### Post by ninjasinloaf on 2011-04-09
I found a .deb package already made here: [https://launchpad.net/~janvitus/+archive/ppa/+buildjob/2436460](https://launchpad.net/~janvitus/+archive/ppa/+buildjob/2436460) by googling tomboy 1.6 deb, and there's some for the amd also.

I couldn't get it to work because I didn't have some of the dependencies satisfied.  I also have Lucid, so maybe that's why because this thing has "natty" written at the end.  But maybe better luck for you.

---

### Post by _nikolaos on 2011-04-09
Thanks for the quick answer.
I thought erroneously that the awn-applet is somewhere in tomboy. So I'll look for this elsewhere now.

As for the tomboy upgrade, of course it would be great to install it effortlessly from the repositories, but I already chose a hard way for this job. Do you think that I should stop, delete the folder and try again from the repositories later? I really wish that I could make it to the end, in the console.

---

### Post by _nikolaos on 2011-04-09
> **ninjasinloaf said:**
> I found a .deb package already made here: [https://launchpad.net/~janvitus/+archive/ppa/+buildjob/2436460](https://launchpad.net/~janvitus/+archive/ppa/+buildjob/2436460) by googling tomboy 1.6 deb, and there's some for the amd also.

I couldn't get it to work because I didn't have some of the dependencies satisfied.  I also have Lucid, so maybe that's why because this thing has "natty" written at the end.  But maybe better luck for you.

Just downloaded this, and Package Installer (in GNOME) is demanding:
```
Error: Dependency is not satisfiable: libc6 (>= 2.12)|libc6.1 (>= 2.12)|libc0.1 (>= 2.12)
```

Is it wrong to install these libraries in my own Lucid? Did you try as well and saw that it kept on showing errors?

---

### Post by ninjasinloaf on 2011-04-09
I tried to download the dependencies from Synaptic, but it said that they were already up to date and that the latest version was installed.  I haven't tried to go find them because I haven't the time today, but I've been successful with things like this in the past.  My initial problem (which was that 1.4 randomly began crashing at startup, which is why I went looking for an upgrade) was solved by uninstalling, deleting the tomboy folder in /home/.local and then reinstalling and re-sync-ing my notes.  Not that you needed to know all of that, but in case someone did!

I'll probably try this way of upgrading in the near future, so let me know if it works!

---

### Post by sharm on 2011-04-15
Wait for the Tomboy PPA to be updated, upgrade to Natty, or uninstall the Tomboy package and build from source using these instructions:

[https://live.gnome.org/Tomboy/Developers](https://live.gnome.org/Tomboy/Developers)

Using random debs that you find that aren't meant for your distro will end up not making you happy.  I recommend waiting for the PPA.

FWIW, 1.6.0 does not have many user-visible changes from 1.4.x, so as a user I think you'd be quite happy upgrading to 1.4.2 in the PPA.  Then you'll automatically get 1.6.0 when our packager has that ready, too.

---

### Post by _nikolaos on 2011-04-17
> **sharm said:**
> FWIW, 1.6.0 does not have many user-visible changes from 1.4.x, so as a user I think you'd be quite happy upgrading to 1.4.2 in the PPA.  Then you'll automatically get 1.6.0 when our packager has that ready, too.

I think I will follow your suggestion and just wait for the upgrade to get ready. Thanks.

---

### Post by AuraAeolian on 2012-12-25
Hi
i'd like to upgrade tomboynotes on lucid, but i don't know how...
here you can find the new packages...
[https://launchpad.net/~tomboy-packagers/+archive/stable](https://launchpad.net/~tomboy-packagers/+archive/stable)
now how to install them???
if i have already "added this ppa to my system"...
thanks for further step by step instructions ):P

---

### Post by overdrank on 2012-12-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

