---
title: "how can I find the path to dependencies"
date: 2010-09-24
forum: General Help
---

### Post by coolgenes on 2010-09-24
I am trying to install Staden on a Ubuntu 10.04 machine (64bit).  It requires a number of dependencies to be installed prior to configuring the source.  I was fortunate to find all of them using the synaptic package manager.  now for the configure command I need to specify where these dependencies are as options.  

My question is how do I find the programs that I need to reference as options to the configure command such as: tcl, tk, zlib, xz utils, libpng, curl, tklib, itcl, itk, etc.  Is there a standard directory that synaptic uses or what?

---

### Post by btindie on 2010-09-24
The *configure* command should find most of the files it requires, if it doesn't it will let you know. Have you tried running it yet? Was it able to find them??
 
The header files are stored under /usr/include, and the libraries are generally under /usr/lib.
 
If you want to find the location a certain package installs files then use the *dpkg* command.
 
**dpkg -l** | **--list** *package-name-pattern* ... List packages matching given pattern. If no *package-name-pattern* is given, list all packages in */var/lib/dpkg/available*. Normal shell wildchars are allowed in *package-name-pattern*. (You will probably have to quote *package-name-pattern* to prevent the shell from performing filename expansion. For example, **dpkg -l 'libc5*'** will list all the package names starting with "libc5".)
 
**dpkg -L** | **--listfiles** *package* ... List files installed to your system from **package**. However, note that files created by package-specific installation-scripts are not listed.

---

### Post by coolgenes on 2010-09-26
So this first time trying the configure I tried to use gedit to specify the location of the dependencies that I could find.  This is the result of that attempt.  Please keep in mind that I didn't specify all of them, and I did install all the dependencies that Staden specified.  Here is the output, if you can suggest anything that I can do to improve it please let me know.  I'll try the list functions that you recommend as soon as I get to the computer Monday morning

/configure LIBS=-lgfortranchecking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for gawk... gawk
checking for curl-config... no
checking whether libcurl is usable... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for inflateEnd in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for lzma_easy_buffer_encode in -llzma... no
configure: WARNING: "--with-lzma specified
configure: WARNING: "No functioning lzma found"
configure: WARNING: No liblzma detected. Gap5 may be able to read some database. To fix this please install liblzma and rerun configure using the --with-lzma=DIR option.
checking for png_create_write_struct in -lpng... no
configure: WARNING: "--with-png specified
configure: WARNING: "No functioning png found"
configure: WARNING: No PNG library found. Gap4's Report Mutatations functionality will be absent.
checking for bam_header_read in -lbam... no
configure: WARNING: No functioning samtools found
configure: WARNING: Gap5/tg_index will have reduced functionality
checking for staden-io_lib-config... no
checking for io_lib-config... /usr/bin/io_lib-config
checking if io_lib version >= 1.12.2... yes
checking for mvwprintw in -lncurses... no
checking for mvwprintw in -lcurses... no
configure: WARNING: "--with-curses specified
configure: WARNING: "No functioning curses found"
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for unistd.h... (cached) yes
checking for zlib.h... (cached) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for library containing cos... none required
checking for popen... yes
checking for X... no
checking whether byte ordering is bigendian... no
checking for correct TEA configuration... ok (TEA 3.7)
checking for Tcl configuration... found /usr/lib/tcl8.5/tclConfig.sh
checking for existence of /usr/lib/tcl8.5/tclConfig.sh... loading
checking for Tk configuration... configure: error: Can't find Tk configuration definitions

---

### Post by btindie on 2010-09-27
It looks like a number of required libraries are not installed or have not been installed correctly. Take a look at the [following]("https://help.ubuntu.com/community/CompilingSoftware"), it may shed some light on how to fix it.

---

### Post by nothingspecial on 2010-09-27
You need to install a compiler before you compile

```
sudo apt-get install build-essential
```

---

### Post by btindie on 2010-09-27
You first need to build the staden-io_lib tar ball as standen depends on that. It appears that that exists in the Ubuntu Universe repository so if you enable the [Universe repository]("https://help.ubuntu.com/community/Repositories/CommandLine") you'll be able to install the io_lib with ```
sudo apt-get install staden-io-lib-utils libstaden-read-dev
```
 
To install some of the other libraries that are available in the repositories run
```
sudo apt-get install liblzma-dev libncurses5-dev zlib1g-dev libcurl3-dev libpng12-dev tcl-dev tk-dev libxt-dev itcl3-dev itk3-dev tcllib tklib gfortran
```
 
Some of these again are in the Universe repository which isn't enabled by default.
 
Run *./configure* again and see what it complains about then.

---

### Post by coolgenes on 2010-09-27
thanks for everyone who has posted so far.  I think I need to make one thing more clear.  I have already installed all the dependencies listed by Staden's README.build. including staden-io_lib, samtools, tcl, tk, zlib, xzutils, libpng, curl, tklib, itcl, itk, iwidgets, gcc, g++ gfortran and f2c.c using the apt-get install.  How can it be installed incorrectly if using synaptic?  At present I am installing in /usr/local/genome/Staden.  Is this too far from where the dependencies may be installed that the Staden configure can't find them.  Should I try the installation somewhere else?

---

### Post by btindie on 2010-09-27
The output from configure shows that it's unable to find some of the required libraries. I find that unlikely if you've installed them through apt which would have put them in the standard location.
 
From this error it appears that you are telling it where to find the lzma files, what is the configure command line you are using??
```
configure: WARNING: "--with-lzma specified
```
From looking at the *configure* source, if you are going to specify that option you need to set it to
```
--with-lzma=/usr
```
along with the other ones you've specified. Though as they're in the standard location there shouldn't be any need to.

---

