---
title: "gstreamer installation problems"
date: 2006-04-01
forum: General Help
---

### Post by sparks5oh on 2006-04-01
I am pretty New at linux and trying to install gstreamer but at the end it is saying I do not have libxml but when I do a sudo apt-get install libxml2 it says I have the latest verison can any one help me out:( 

checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for VALGRIND... no
configure: Using GStreamer source release as package name
configure: Using Unknown package origin as package origin
configure: Using /usr/local/var/cache/gstreamer-0.10 as registry cache dir
configure: WARNING: Sissy ! By asking to not build the tests known to fail, you hereby waive your right to customer support.  If you do not agree with this EULA, please press Ctrl-C before the next line is printed.  By allowing the next line to be printed, you expressly acknowledge your acceptance of this EULA.
checking whether byte ordering is bigendian... no
checking if unaligned memory access works correctly... (whitelisted) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gawk... (cached) mawk
checking for bison... /usr/bin/bison
checking bison version... ok
checking for flex... /usr/bin/flex
checking for perl... /usr/bin/perl
checking for valgrind... no
configure: Looking for Python version >= 2.1
checking for python... /usr/bin/python
checking "/usr/bin/python":... okay
checking local Python configuration... looks good
checking for library containing strerror... none required
checking for ANSI C header files... (cached) yes
checking ucontext.h usability... yes
checking ucontext.h presence... yes
checking for ucontext.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking process.h usability... no
checking process.h presence... no
checking for process.h... no
checking for inline... inline
checking to see if compiler understands -fno-common... yes
checking for sigaction... yes
checking for _LARGEFILE_SOURCE value needed for large files... 1
checking for fseeko... yes
checking for ftello... yes
checking for fgetpos... yes
checking for fsetpos... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether gcc implements __PRETTY_FUNCTION__... yes
checking whether gcc implements __FUNCTION__... yes
checking whether gcc implements __func__... yes
checking for register_printf_function... yes
checking for dladdr in -ldl... yes
checking for GLIB... yes
checking glib version >= 2.8... yes
checking for GLIB_ONLY... yes
checking for XML... configure: error: Need libxml2 for glib2 builds -- you should be able to do without it -- this needs fixing

---

### Post by Sutekh on 2006-04-01
Why are you trying to compile gstreamer?  It is available for donwloading via apt-get.

In regards to that error you need the development files for XML
```
sudo apt-get install libxml2-dev
```

---

### Post by sparks5oh on 2006-04-01
I didn't know you can donwload it apt-get what is the command

---

### Post by Sutekh on 2006-04-01
What in particular do you need?  There are a number of available packages for different things.

---

### Post by sparks5oh on 2006-04-01
gstreamer

---

### Post by Sutekh on 2006-04-01
Yeah but what for? 

Here is the list of gstreamer packages, there are a lot.

[Ubuntu Packages - gstreamer]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gstreamer&searchon=names&subword=1&version=breezy&release=all")

I just want to know what you need.

---

### Post by sparks5oh on 2006-04-01
Oh sorry I'm just starting at linux and don't really know what I'm doing quite yet. what i want to do is install listen and it says gstreamer is a dependency

---

### Post by Ramses de Norre on 2006-04-01
What's the program listen for? It's not in the repo's.
If you want to listen to mp3's, wma, etc check this: [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Sutekh on 2006-04-01
Okay if you want listen here's how you should go about getting it

Backup and edit your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
Then according to [http://listengnome.free.fr/](http://listengnome.free.fr/) add this line to your repositories list
```
deb http://theli.free.fr/packages/breezy/ ./
```
Then save the file (Ctrl+O) and exit (Ctrl+X)

Refresh the repositories and install listen
```
sudo apt-get update
sudo apt-get install listen
```
The rest will be taken care of

If you want to play mp3's you need to install the gstreamer0.8-mad package

It's in the universe repositories, so you will need to edit the sources.list again, and uncomment the lines containing **universe**.  Just remove the # signs to do this.  

Save and refresh the repositories and install the package with
```
sudo apt-get update
sudo apt-get install gstreamer0.8-mad
```

---

### Post by engla on 2006-04-01
[QUOTE=sparks5oh]Oh sorry I'm just starting at linux and don't really know what I'm doing quite yet. what i want to do is install listen and it says gstreamer is a dependency[/QUOTE]
Yep, I know listen, I use it. Listen needs gstreamer, which is in all ubuntu installs.

However, the latest listen (0.4.*) requires the latest gstreamer (0.10), and that's only available in dapper, the development branch for the next release of ubuntu.

So the only way to use listen is then to either use dapper or to compile gstreamer yourself, and I don't think that's very easy, in short, don't try.

Listen 0.3.* only requires gstreamer 0.8, so you have to stay with that :-(

Yeah, I know, I was also disappointed when the developer chose to obsolete breezy badger ubuntu before the next version is even released!

---

