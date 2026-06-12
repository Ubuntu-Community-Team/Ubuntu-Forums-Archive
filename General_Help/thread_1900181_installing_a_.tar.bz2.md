---
title: "installing a .tar.bz2"
date: 2011-12-25
forum: General Help
---

### Post by yoramdavid on 2011-12-25
Hello all,

I want to install Rubrica and downloaded the version rubrica2-2.0.10 from here: [http://linux.softpedia.com/dyn-postdownload.php?p=3898&t=0&i=1](http://linux.softpedia.com/dyn-postdownload.php?p=3898&t=0&i=1), but it comes in a tar.bz2 format.

I have extracted and inside the folder there are instructions to install as follows:

```
1. `cd' to the directory containing the package's source code and type   `./configure' to configure the package for your system.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

```

1- The first step gave me an error:
```
The intltool scripts were not found. Please install intltool.
```
So I installed intltool and ran the ./configure again and got a new error:

```
Package requirements (gobject-2.0 gmodule-2.0 glib-2.0 libxml-2.0) were not met:
```

I tried to install it but there is no such package:
```
E: Não foi possível encontrar o pacote libxml-2.0
E: Não foi possível encontrar o pacote através da expressão regular 'libxml-2.0'
```

2- I tried step two of the installation any way, which gives me the error:
```
make
make: *** Nenhum alvo indicado e nenhum arquivo make encontrado.  Pare.
```
Meaning there is no target indicated and no archive "make" found

3 - Step 3... :
```
make install
make: *** Sem regra para processar o alvo `install'.  Pare
```
Meaning no rules to process target "install"

How am I supposed to install this package?

Thank in advance for your time.

Yoram

---

### Post by westie457 on 2011-12-25
No idea how you got a tar file. Have just downloaded from the link you posted and got a .deb file.

---

### Post by yoramdavid on 2011-12-25
> **westie457 said:**
> No idea how you got a tar file. Have just downloaded from the link you posted and got a .deb file.

You are right, I posted the wrong link. That link also gave me a .deb but it was 32 bits, I need 64 bits.

I will update the link above.

I do have a tar.gz2 file

Yoram

---

### Post by mörgæs on 2011-12-25
Why don't you install from the repositories?

---

### Post by yoramdavid on 2011-12-25
> **mörgæs said:**
> Why don't you install from the repositories?

Thank you mörgæs,

yes, I have installed it from the repositories, but the author told me that it is an old version and recommended me to install the new one since I am having issues with the old one.

---

### Post by azmyth on 2011-12-25
Look in the config.log file to see what it was looking for to give you the error.

---

### Post by yoramdavid on 2011-12-25
> **azmyth said:**
> Look in the config.log file to see what it was looking for to give you the error.

Thank you azmyth,

I will paste here all the lines with error, the log is quite long to put here (some of the errors are repeated more than once):
```
g++: error: unrecognized option '-V'
...
g++: fatal error: no input files
g++: error: unrecognized option '-qversion'
g++: fatal error: no input files
...
conftest.c:11:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
...
conftest.c:65:20: error: expected expression before ')' token
...
configure:15815: $PKG_CONFIG --exists --print-errors "gobject-2.0 gmodule-2.0 glib-2.0 libxml-2.0"
Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
...
configure:15863: error: Package requirements (gobject-2.0 gmodule-2.0 glib-2.0 libxml-2.0) were not met:

No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBRAL_CFLAGS
and LIBRAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
...
ac_cv_search_strerror='none required'

```

Shall I paste the whole log here?

Yoram

---

### Post by wildmanne39 on 2011-12-25
Hi, make sure build-essentials, linux-kernel headers and dkms is installed hopefully that will take care of the problem.
Thanks

---

### Post by yoramdavid on 2011-12-25
> **wildmanne39 said:**
> Hi, make sure build-essentials, linux-kernel headers and dkms is installed hopefully that will take care of the problem.
Thanks

Thank you wildmanne,

I have the following installed:
*build-essential
*linux-header-generic (could not find something with the name of linux-kernel headers
*dkms

yoram

---

### Post by azmyth on 2011-12-25
Try installing

sudo apt-get install libxml2

and if this doesn't work try

sudo apt-get install libxml2-dev

then try again

---

### Post by wildmanne39 on 2011-12-25
Hi, that is the one, it looks like I remembered the name wrong, just make sure you are using the generic kernel if that is the one you have installed, you can check with.
```
uname -a
```
Thanks

---

### Post by yoramdavid on 2011-12-25
> **azmyth said:**
> Try installing

sudo apt-get install libxml2

and if this doesn't work try

sudo apt-get install libxml2-dev

then try again

libxml2 was already installed, libxml2.dev was not but still it does not work. I wonder if this package was 32bits, and my system is 64bits...

---

### Post by yoramdavid on 2011-12-25
> **wildmanne39 said:**
> Hi, that is the one, it looks like I remembered the name wrong, just make sure you are using the generic kernel if that is the one you have installed, you can check with.
```
uname -a
```
Thanks

Thank you,

I think yes:

```
uname -a
Linux yoram-II 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by yoramdavid on 2011-12-26
I just got a message from the author of Rubrica:

<quote>
Hello Yoram,

rubrica is developed on redhat/fedora system I neved tested on debian/ubuntu, binaries availables on my sites are only for 32 bits. If you want 64 bit binaries you must get rubrica's debian package (but it is old too) or compile it by yourself. It is easy to do if you have development tools (install from synaptic all you need) then get source (tarball) and see README/INSTALL

anyway you must:
./configure --prefix=/path/where/you/want/to/install (usually --prefix=/usr)
make
sudo make install

or ask someone in debian world to upgrade to last release
</quote>

The install file has the followig information:

```
1. `cd' to the directory containing the package's source code and type     `./configure' to configure the package for your system.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.
```

Can someone help me with this?
"or ask someone in debian world to upgrade to last release" - that would be great!

Regards,

Yoram

---

### Post by azmyth on 2011-12-27
Try installing ia32-libs

sudo apt-get install ia32-libs

then try again

---

### Post by yoramdavid on 2011-12-27
> **azmyth said:**
> Try installing ia32-libs

sudo apt-get install ia32-libs

then try again

Thank you azmyth,

ia32-libs was already installed.

Any other suggestions?

---

### Post by azmyth on 2011-12-27
Sorry I'm out of suggestions. Hopefully someone else can help.

---

### Post by yoramdavid on 2011-12-28
> **azmyth said:**
> Sorry I'm out of suggestions. Hopefully someone else can help.

OK, thank you, I hope too :)

---

### Post by azmyth on 2011-12-28
You should recheck to make sure you've installed the libxml2. As I have the same exact kernel and I was able to get it past the config stage. Anyhow, it doesn't matter as there are errors in the code to prevent it from compiling properly.

---

### Post by yoramdavid on 2011-12-28
> **azmyth said:**
> You should recheck to make sure you've installed the libxml2. As I have the same exact kernel and I was able to get it past the config stage. Anyhow, it doesn't matter as there are errors in the code to prevent it from compiling properly.

I checked again:

```
sudo apt-get install libxml2
[sudo] password for yoram: 
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
libxml2 já está na versão mais recente.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 11 não actualizados.

```

libxml2 already on the most recent version.

---

### Post by yoramdavid on 2012-01-05
OK, I have made some improvements.

I installed three programs:

1 - libgconf2-dev_3.2.3-0ubuntu0.1_amd64.deb
2 - libglade2-dev_1%3a2.6.4-1build1_amd64.deb
3 - libnotify-dev_0.7.4-1_amd64.deb

Then the command "./configure" again:

```
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.12.4
checking for XML::Parser... ok
configure: WARNING: Libtool does not cope well with whitespace in `pwd`
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for library containing strerror... none required
checking for ANSI C header files... (cached) yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether time.h and sys/time.h may both be included... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking for localtime_r... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBRAL... yes
checking for RUBRICA... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking for libintl.h... (cached) yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  de el en_US fr it uk
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gtkdoc-check... no
checking for gtkdoc-rebase... no
checking for gtkdoc-mkpdf... no
checking whether to build gtk-doc documentation... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating rubrica2.spec
config.status: creating rubrica2.desktop
config.status: creating rubrica2.schemas
config.status: creating rubrica2.keys
config.status: creating pixmaps/Makefile
config.status: creating pixmaps/16x16/Makefile
config.status: creating pixmaps/22x22/Makefile
config.status: creating pixmaps/24x24/Makefile
config.status: creating pixmaps/48x48/Makefile
config.status: creating pixmaps/scalable/Makefile
config.status: creating interface/Makefile
config.status: creating doc/Makefile
config.status: creating doc/reference/Makefile
config.status: creating po/Makefile.in
config.status: creating libral/Makefile
config.status: creating libral/libral.pc
config.status: creating src/Makefile
config.status: creating plugins/Makefile
config.status: creating plugins/csv/Makefile
config.status: creating plugins/rubrica/Makefile
config.status: creating plugins/vcard/Makefile
config.status: creating plugins/gmail/Makefile
config.status: creating test/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands


Configuration:
        Package name:           rubrica2
        Web page:               www.nicolafragale.org
        Version:                2.0.10

        Plugins dir:            $(libdir)/libral/plugins
        Plugins gui dir:        $(datadir)/libral/plugins/gui
        Pixmap  dir:            ${datarootdir}/pixmaps
        Icons   dir:            ${datarootdir}/pixmaps/rubrica2
        Config  dir:            ${prefix}/etc/gconf/schemas
        Code name: 
```

I see no errors there.

But I get errors with the next step: "make"
```
make
make  all-recursive
make[1]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10'
Making all in libral
make[2]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
Making all in src
make[2]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
make[3]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2 -I/usr/include/gconf/2   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml2    -DGTK_COMPILATION -DGTK_DISABLE_DEPRECATED=1 -DGDK_DISABLE_DEPRECATED=1 -DGDK_PIXBUF_DISABLE_DEPRECATED=1 -DG_DISABLE_DEPRECATED=1 -DGETTEXT_PACKAGE=\""rubrica2"\" -DRUBRICA_LOCALE_DIR=\""/usr/local/share/locale"\" -DRUBRICA_PIXMAPS_DIR=\""/usr/local/share/pixmaps"\" -DRUBRICA_ICONS_DIR=\""/usr/local/share/pixmaps/rubrica2"\" -DRUBRICA_PLUGINS_DIR=\"""\" -DRUBRICA_GUI_DIR=\""/usr/local/share/rubrica2/interface"\" -DRUBRICA_DOC_DIR=\""/usr/local/share/doc/"\" -DRUBRICA_HANDBOOK=\""/usr/local/share/doc/rubrica2/html"\" -DRUBRICA_VERSION=\""2.0.10"\" -DRUBRICA_CODE_NAME=\"""\" -DRUBRICA_INFO_CODE_NAME=\"""\" -DRUBRICA_WEB_PAGE=\""www.nicolafragale.org"\" -I.. -I.. -I../libral -I../libral   -DHAVE_CONFIG_H -Wall -g  -g -O2 -MT app.o -MD -MP -MF .deps/app.Tpo -c -o app.o app.c
app.c: Na função ‘rubrica_app_init’:
app.c:1273:11: erro: too many arguments to function ‘notify_notification_new’
/usr/include/libnotify/notification.h:114:21: nota: declared here
app.c: Na função ‘rubrica_app_show_message’:
app.c:1924:8: aviso: format not a string literal and no format arguments [-Wformat-security]
make[3]: ** [app.o] Erro 1
make[3]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10'
make: ** [all] Erro 2
```

I have no idea what those errors are! Do I need to be sudo?

I try the command "make check" to run tests:
```
make check
Making check in libral
make[1]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
make[1]: Nada a ser feito para `check'.
make[1]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
Making check in src
make[1]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
make[2]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2 -I/usr/include/gconf/2   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml2    -DGTK_COMPILATION -DGTK_DISABLE_DEPRECATED=1 -DGDK_DISABLE_DEPRECATED=1 -DGDK_PIXBUF_DISABLE_DEPRECATED=1 -DG_DISABLE_DEPRECATED=1 -DGETTEXT_PACKAGE=\""rubrica2"\" -DRUBRICA_LOCALE_DIR=\""/usr/local/share/locale"\" -DRUBRICA_PIXMAPS_DIR=\""/usr/local/share/pixmaps"\" -DRUBRICA_ICONS_DIR=\""/usr/local/share/pixmaps/rubrica2"\" -DRUBRICA_PLUGINS_DIR=\"""\" -DRUBRICA_GUI_DIR=\""/usr/local/share/rubrica2/interface"\" -DRUBRICA_DOC_DIR=\""/usr/local/share/doc/"\" -DRUBRICA_HANDBOOK=\""/usr/local/share/doc/rubrica2/html"\" -DRUBRICA_VERSION=\""2.0.10"\" -DRUBRICA_CODE_NAME=\"""\" -DRUBRICA_INFO_CODE_NAME=\"""\" -DRUBRICA_WEB_PAGE=\""www.nicolafragale.org"\" -I.. -I.. -I../libral -I../libral   -DHAVE_CONFIG_H -Wall -g  -g -O2 -MT app.o -MD -MP -MF .deps/app.Tpo -c -o app.o app.c
app.c: Na função ‘rubrica_app_init’:
app.c:1273:11: erro: too many arguments to function ‘notify_notification_new’
/usr/include/libnotify/notification.h:114:21: nota: declared here
app.c: Na função ‘rubrica_app_show_message’:
app.c:1924:8: aviso: format not a string literal and no format arguments [-Wformat-security]
make[2]: ** [app.o] Erro 1
make[2]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
make[1]: ** [check-recursive] Erro 1
make[1]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/src'
make: ** [check-recursive] Erro 1
```
Same kind of errors?

I try the last step anyway: "make install":
```
make install
Making install in libral
make[1]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
make[2]: Entrando no diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libral.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libral.so.1.0.0 /usr/local/lib/libral.so.1.0.0
/usr/bin/install: cannot remove `/usr/local/lib/libral.so.1.0.0': Permission denied
make[2]: ** [install-libLTLIBRARIES] Erro 1
make[2]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
make[1]: ** [install-am] Erro 2
make[1]: Saindo do diretório `/media/Documentos/Programas - Linux/Rubrica 2-2.0.10/rubrica2-2.0.10/libral'
make: ** [install-recursive] Erro 1

```

What is wrong now?
Thank you in advance.

---

### Post by yoramdavid on 2012-01-07
Anybody, please?

---

