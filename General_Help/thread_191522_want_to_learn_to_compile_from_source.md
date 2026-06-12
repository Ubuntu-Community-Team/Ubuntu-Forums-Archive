---
title: "want to learn to compile from source"
date: 2006-06-07
forum: General Help
---

### Post by roderikk on 2006-06-07
Hi,

I've no idea where to post this but here it goes. As a relative newby I am trying to get a hang of ubuntu so I wanted to install the newest version of rxvt-unicode so I could also get a cool transparent terminal. However when I try to install it by running ./configure in the directory I unpacked to I first got an error which I solved by sudo apt-get install cpp gpp g++ . However, now I get the following error:

```
checking for /usr/bin/perl suitability... configure: error: no, unable to link
```

Which package should I install now? Is there a list of packages I should install when I want to try and do something like this?

Thanks!

---

### Post by ifokkema on 2006-06-07
[QUOTE=roderikk]Hi,

I've no idea where to post this but here it goes. As a relative newby I am trying to get a hang of ubuntu so I wanted to install the newest version of rxvt-unicode so I could also get a cool transparent terminal. However when I try to install it by running ./configure in the directory I unpacked to I first got an error which I solved by sudo apt-get install cpp gpp g++ . However, now I get the following error:

```
checking for /usr/bin/perl suitability... configure: error: no, unable to link
```

Which package should I install now? Is there a list of packages I should install when I want to try and do something like this?

Thanks![/QUOTE]

Before you can compile from source, you need more than just g++ and such. Install build-essential.
```
sudo apt-get install build-essential
```

Hope this helps,

Ivo

---

### Post by roderikk on 2006-06-07
Nope... still get the same error. I don't know whether this is overkill, but here is the entire output:

```
./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu

configuring for rxvt 7.7

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for egrep... grep -E
checking for AIX... no
checking for library containing strerror... none required
checking for working libsupc++... ok
checking for setlocale... yes
checking for gethostbyname... yes
checking for socket... yes
checking for mv... /bin/mv
checking for cp... /bin/cp
checking for ln... /bin/ln
checking for sed... /bin/sed
checking for echo... /bin/echo
checking for cmp... /usr/bin/cmp
checking for tic... /usr/bin/tic
checking how to run the C++ preprocessor... g++ -E
checking for X... no
checking for libXpm... no
checking for sys/wait.h that is POSIX.1 compatible... yes
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
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking sys/byteorder.h usability... no
checking sys/byteorder.h presence... no
checking for sys/byteorder.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking sys/strredir.h usability... no
checking sys/strredir.h presence... no
checking for sys/strredir.h... no
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for stdint.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking cwchar usability... yes
checking cwchar presence... yes
checking for cwchar... yes
checking clocale usability... yes
checking clocale presence... yes
checking for clocale... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether termios.h and sys/ioctl.h may both be included... yes
checking for -rpath dynamic library path recording... no
checking for -R dynamic library path recording... no
checking for XPointer... no
checking for XLIB_ILLEGAL_ACCESS... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for mode_t... yes
checking for pid_t... yes
checking for uid_t in sys/types.h... yes
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long long... yes
checking size of long long... 8
checking for int *... yes
checking size of int *... 4
checking for int16_t... yes
checking for uint16_t... yes
checking for int32_t... yes
checking for uint32_t... yes
checking return type of signal handlers... void
checking for unsetenv... yes
checking for setutent... yes
checking for on_exit... yes
checking for ttyslot... yes
checking for updwtmp... yes
checking for updwtmpx... yes
checking utmp.h usability... yes
checking utmp.h presence... yes
checking for utmp.h... yes
checking utmpx.h usability... yes
checking utmpx.h presence... yes
checking for utmpx.h... yes
checking lastlog.h usability... yes
checking lastlog.h presence... yes
checking for lastlog.h... yes
checking for utmp.h... (cached) yes
checking for struct utmp... yes
checking for ut_host in utmp struct... yes
checking for ut_pid in utmp struct... yes
checking for utmpx.h... (cached) yes
checking for struct utmpx... yes
checking for host in utmpx struct... yes
checking for session in utmpx struct... yes
checking for struct lastlog... yes
checking for struct lastlogx... no
checking where utmp is located... /var/run/utmp
checking where utmpx is located... /var/run/utmp
checking where wtmp is located... /var/log/wtmp
checking where wtmpx is located... /var/log/wtmp
checking where lastlog is located... /var/log/lastlog
checking where lastlogx is located...
  utmp support:               enabled
  utmp file:                  /var/run/utmp
  utmpx file:                 /var/run/utmp
  wtmp file:                  /var/log/wtmp
  wtmpx file:                 /var/log/wtmp
  lastlog file:               /var/log/lastlog
  lastlogx file:
checking where ttys/ttytab is located...
checking for working Xlocale... no
checking for working X setlocale... no
checking for working plain setlocale... yes
checking for working nl_langinfo... yes
checking for unix-compliant filehandle passing ability... yes
checking for broken XIM callback... no
checking pty.h usability... yes
checking pty.h presence... yes
checking for pty.h... yes
checking util.h usability... no
checking util.h presence... no
checking for util.h... no
checking libutil.h usability... no
checking libutil.h presence... no
checking for libutil.h... no
checking for sys/ioctl.h... (cached) yes
checking sys/stropts.h usability... yes
checking sys/stropts.h presence... yes
checking for sys/stropts.h... yes
checking for revoke... no
checking for _getpty... no
checking for getpt... yes
checking for posix_openpt... yes
checking for isastream... yes
checking for setuid... yes
checking for seteuid... yes
checking for setreuid... yes
checking for setresuid... yes
checking for /dev/ptym/clone... no
checking for /dev/ptc... no
checking for /dev/ptmx... yes
checking for UNIX98 ptys... yes
checking for tty group... yes
checking for pkg-config... /usr/bin/pkg-config
checking for xft-config... no
checking X11/Xft/Xft.h usability... no
checking X11/Xft/Xft.h presence... no
checking for X11/Xft/Xft.h... no
checking for XftDrawString32 in -lXft... no
checking for perl5... no
checking for perl... /usr/bin/perl
checking for /usr/bin/perl suitability... configure: error: no, unable to link

```

---

### Post by tonyr on 2006-06-07
**configure** should have left a **config.log** file around.  See if you can make any
snese out of that, or gzip it and attach it to a post here.

---

### Post by roderikk on 2006-06-07
[QUOTE=tonyr]**configure** should have left a **config.log** file around.  See if you can make any
snese out of that, or gzip it and attach it to a post here.[/QUOTE]

You were right to assume I wouldn't be able to make any sense out of it :roll: ... I see some errors here and there, but I'll just attach it. Thanks for the help!

---

### Post by tonyr on 2006-06-07
One step ahead.  I downloaded **rxvt-unicode** source and ran the **configure**.
It looks like a **jump-in-the-deepend** type of learning experience.  The **configure**
command you should use is
```

./configure --disable-perl --disable-xpm-background

```

I found some clues in the file **README.configure**.   Figuring out how to read
that is a lesson in itself.  The **perl** business is about
including an embedded **perl** interpreter, so you would need to figure out what is
involved in that.  The **xpm** thing turned up after I added the **--disable-perl** option,
and to use that you would need to, again, figure out what all that is about.  I usually
follow the rule-of-thumb: "If it is optional and I don't absolutely need it, I don't use it".

---

### Post by ifokkema on 2006-06-08
[QUOTE=roderikk]You were right to assume I wouldn't be able to make any sense out of it :roll: ... I see some errors here and there, but I'll just attach it. Thanks for the help![/QUOTE]

Although you seem to have resolved the problem using the --disable-perl flag, I was trying to figure out the log you send. It seems to me it's trying to link to a perl.h, but fails. The only package in my repositories which has a perl.h file, is the package 'perl'. Is that installed on your system? If not, installing that package might help you out.

---

### Post by thasheep on 2006-06-08
I'd be surprised if perl.h isn't in the package libperl-dev.

---

### Post by ifokkema on 2006-06-08
[QUOTE=thasheep]I'd be surprised if perl.h isn't in the package libperl-dev.[/QUOTE]

According to this, it doesn't:
```
  ifokkema@5-HKG-02-0098:~$ apt-file show libperl-dev
libperl-dev: usr/lib/libperl.a
libperl-dev: usr/lib/libperl.so
libperl-dev: usr/share/doc/libperl-dev
  ifokkema@5-HKG-02-0098:~$ sudo apt-get install -d libperl-dev
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libperl-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 560kB of archives.
After unpacking 1434kB of additional disk space will be used.
Get:1 http://uk.archive.ubuntu.com dapper/main libperl-dev 5.8.7-10ubuntu1 [560kB]
Fetched 560kB in 0s (1536kB/s)
Download complete and in download only mode
  ifokkema@5-HKG-02-0098:~$ dpkg --contents /var/cache/apt/archives/libperl-dev_5.8.7-10ubuntu1_i386.deb
drwxr-xr-x root/root         0 2005-12-16 09:11:55 ./
drwxr-xr-x root/root         0 2005-12-16 09:11:37 ./usr/
drwxr-xr-x root/root         0 2005-12-16 09:11:37 ./usr/lib/
-rw-r--r-- root/root   1399024 2005-12-16 09:11:36 ./usr/lib/libperl.a
drwxr-xr-x root/root         0 2005-12-16 09:11:37 ./usr/share/
drwxr-xr-x root/root         0 2005-12-16 09:11:37 ./usr/share/doc/
lrwxrwxrwx root/root         0 2005-12-16 09:11:37 ./usr/lib/libperl.so -> libperl.so.5.8
lrwxr-xr-x root/root         0 2005-12-16 09:11:37 ./usr/share/doc/libperl-dev -> perl

```

---

### Post by thasheep on 2006-06-08
[QUOTE=ifokkema]According to this, it doesn't:[/QUOTE]I stand corrected. Nonetheless, I'd suggest installing libperl-dev for building a terminal with an embedded perl interpreter. Its description says [quote=apt-cache show libperl-dev]Perl library: development files
 Files for developing applications which embed a Perl interpreter and for
 programs compiled with perlcc.[/quote]

---

### Post by tonyr on 2006-06-08
I can confirm it.  Installing **libperl-dev** allows the 'perl suitability' check to
succeed.  I still used the **--disable-xpm-background** option.  There is probably a
**libxpm-dev** package, or something like that, that would take care of that, too.
Here is the end of my configure output:

```

Configuration:

  Rxvt version:               7.7 : 2006-02-21
  Source code location:       .
  Install path:               /usr/local/bin
  Compiler:                   g++
  Compiler flags:             -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs
  Linker:                     gcc
  default resource name:      urxvt
  resource class:             URxvt
  resource class fallback:    Rxvt

  embedded perl:              yes

*** Optionally check src/feature.h for further, rarely used options ***

```

---

### Post by roderikk on 2006-06-08
Hi,

Thanks for all the help! However, first I tried running it with the perl/xml disabled options. Then make gave an error. So I installed the libperl-dev package and I could just run ./configure to get to the end with this output:

```
Configuration:

  Rxvt version:               7.7 : 2006-02-21
  Source code location:       .
  Install path:               /usr/local/bin
  Compiler:                   g++
  Compiler flags:             -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs
  Linker:                     gcc
  default resource name:      urxvt
  resource class:             URxvt
  resource class fallback:    Rxvt

  embedded perl:              yes

.----------------------------------------------------------------.
. WARNING: --enable-xpm-background was specified however the     .
.          XPM includes files and libraries could not be found.  .
.          XPM backgrounds are now being DISABLED!  If you want  .
.          to use them you should rerun   configure   with the   .
.          appropriate --with-xpm-includes=/path/to/xpm/includes .
.          and --with-xpm-library=/path/to/xpm/library lines.    .
.----------------------------------------------------------------.
.----------------------------------------------------------------.
. WARNING: --enable-xim was specified however the locale support .
.          functions could not be found.                         .
.          XIM is now being DISABLED!                            .
.----------------------------------------------------------------.
*** Optionally check src/feature.h for further, rarely used options ***

```

It does show the XIM option but says it disabled it itself. However, the problem still remains that when I run make I get this output:

```
 make
make[1]: Entering directory `/home/roderik/software/rxvt-unicode-7.7/src'
g++ -DHAVE_CONFIG_H   -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs  -DDEBUG_STRICT   -I.. -I. -I. -c rxvt.C
In file included from rxvt.h:4,
                 from rxvt.C:24:
rxvtlib.h:34:22: error: X11/Xlib.h: No such file or directory
rxvtlib.h:35:23: error: X11/Xutil.h: No such file or directory
rxvtlib.h:36:27: error: X11/Xresource.h: No such file or directory
In file included from rxvt.C:24:
rxvt.h:28:28: error: X11/cursorfont.h: No such file or directory
rxvt.h:29:24: error: X11/keysym.h: No such file or directory
rxvt.h:30:27: error: X11/keysymdef.h: No such file or directory
rxvt.h:31:23: error: X11/Xatom.h: No such file or directory
rxvt.h:33:22: error: X11/Xmd.h: No such file or directory
rxvtlib.h:137: error: ‘Window’ does not name a type
rxvtlib.h:138: error: ‘Window’ does not name a type
rxvtlib.h:139: error: ‘GC’ does not name a type
rxvtlib.h:140: error: ‘Pixmap’ does not name a type
rxvtlib.h:225: error: ‘Window’ does not name a type
rxvtlib.h:237: error: ‘XSizeHints’ does not name a type
rxvtlib.h:244: error: ‘Cursor’ does not name a type
rxvttoolkit.h:133: error: ‘Drawable’ does not name a type
rxvttoolkit.h:134: error: expected type-specifier before ‘Drawable’
rxvttoolkit.h:141: error: ‘Drawable’ has not been declared
rxvttoolkit.h: In constructor ‘rxvt_drawable::rxvt_drawable(rxvt_screen*, int)’:rxvttoolkit.h:146: error: class ‘rxvt_drawable’ does not have any field named ‘drawable’
rxvttoolkit.h: At global scope:
rxvttoolkit.h:172: error: ISO C++ forbids declaration of ‘Display’ with no type
rxvttoolkit.h:172: error: expected ‘;’ before ‘*’ token
rxvttoolkit.h:174: error: ISO C++ forbids declaration of ‘Visual’ with no type
rxvttoolkit.h:174: error: expected ‘;’ before ‘*’ token
rxvttoolkit.h:175: error: ‘Colormap’ does not name a type
rxvttoolkit.h:206: error: ISO C++ forbids declaration of ‘Display’ with no type
rxvttoolkit.h:206: error: expected ‘;’ before ‘*’ token
rxvttoolkit.h:208: error: ‘Window’ does not name a type
rxvttoolkit.h:210: error: ‘Atom’ does not name a type
rxvttoolkit.h:213: error: ‘Cursor’ does not name a type
rxvttoolkit.h:217: error: ‘XrmDatabase’ does not name a type
rxvttoolkit.h:223: error: ‘Atom’ does not name a type
rxvttoolkit.h:256: error: ‘XEvent’ was not declared in this scope
rxvttoolkit.h:256: error: template argument 2 is invalid
rxvttoolkit.h:257: error: ‘Window’ does not name a type
rxvttoolkit.h:260: error: expected ‘,’ or ‘...’ before ‘(’ token
rxvttoolkit.h:260: error: cannot declare pointer to ‘void’ member
rxvttoolkit.h:264: error: ‘Window’ has not been declared
rxvttoolkit.h: In constructor ‘xevent_watcher::xevent_watcher(O1*, void O2::*)’:rxvttoolkit.h:261: error: ‘XEvent’ was not declared in this scope
rxvttoolkit.h:261: error: template argument 2 is invalid
rxvttoolkit.h: In member function ‘void xevent_watcher::start(rxvt_display*, int)’:
rxvttoolkit.h:266: error: ‘struct xevent_watcher’ has no member named ‘window’
rxvttoolkit.h: At global scope:
rxvttoolkit.h:298: error: ‘XColor’ does not name a type
rxvttoolkit.h:310: error: ‘XColor’ has not been declared
rxvttoolkit.h: In member function ‘rxvt_color::operator Pixel() const’:
rxvttoolkit.h:301: error: ‘c’ was not declared in this scope
rxvt.h: At global scope:
rxvt.h:202: error: ‘Time’ does not name a type
rxvt.h:209: error: ‘CARD32’ does not name a type
rxvt.h:210: error: ‘CARD32’ does not name a type
rxvt.h:211: error: ‘CARD32’ does not name a type
rxvt.h:212: error: ‘INT32’ does not name a type
rxvt.h:213: error: ‘CARD32’ does not name a type
rxvt.h:988: error: ISO C++ forbids declaration of ‘Atom’ with no type
rxvt.h:988: error: expected ‘;’ before ‘*’ token
rxvt.h:991: error: ‘GC’ does not name a type
rxvt.h:996: error: ‘GC’ does not name a type
rxvt.h:1000: error: ‘GC’ does not name a type
rxvt.h:1003: error: ‘GC’ does not name a type
rxvt.h:1008: error: ‘Pixmap’ does not name a type
rxvt.h:1015: error: ‘Time’ does not name a type
rxvt.h:1021: error: ‘Cursor’ does not name a type
rxvt.h:1030: error: ‘XComposeStatus’ does not name a type
rxvt.h:1086: error: ‘XKeyEvent’ has not been declared
rxvt.h:1104: error: ‘XEvent’ has not been declared
rxvt.h:1108: error: ‘XEvent’ has not been declared
rxvt.h:1217: error: ‘XKeyEvent’ has not been declared
rxvt.h:1218: error: ‘XKeyEvent’ has not been declared
rxvt.h:1227: error: ‘XButtonEvent’ has not been declared
rxvt.h:1228: error: ‘XButtonEvent’ has not been declared
rxvt.h:1229: error: ‘XButtonEvent’ has not been declared
rxvt.h:1257: error: ‘Atom’ has not been declared
rxvt.h:1258: error: ‘Atom’ has not been declared
rxvt.h:1399: error: ‘Window’ has not been declared
rxvt.h:1399: error: ‘Atom’ has not been declared
rxvt.h:1400: error: ‘Window’ has not been declared
rxvt.h:1400: error: ‘Atom’ has not been declared
rxvt.h:1401: error: ‘Time’ has not been declared
rxvt.h:1402: error: ‘Atom’ has not been declared
rxvt.h:1404: error: ‘Time’ has not been declared
rxvt.h:1405: error: ‘Time’ has not been declared
rxvt.h:1410: error: expected ‘,’ or ‘...’ before ‘&’ token
rxvt.h:1410: error: ISO C++ forbids declaration of ‘XSelectionRequestEvent’ with no type
rxvt.h:1419: error: ‘Pixmap’ does not name a type
rxvt.h:1421: error: ‘Drawable’ has not been declared
rxvt.h:1453: error: ‘Pixmap’ does not name a type
rxvt.h: In member function ‘void rxvt_term::vt_select_input() const’:
rxvt.h:1100: error: ‘dpy’ was not declared in this scope
rxvt.h:1100: error: ‘vt’ was not declared in this scope
rxvt.h:1100: error: ‘XSelectInput’ was not declared in this scope
make[1]: *** [rxvt.o] Error 1
make[1]: Leaving directory `/home/roderik/software/rxvt-unicode-7.7/src'
make: *** [all] Error 1

```

I see some X11 errors in there... does it have something to do with me running XGL/compiz (just a wild guess... I am really taking a plunge in the deep... :-) ). However, I ám learning... :-)

---

### Post by thasheep on 2006-06-08
Don't worry, nothing to do with XGL/compiz, you just need libx11-dev.
```
sudo apt-get install libx11-dev
```

---

### Post by tonyr on 2006-06-08
Where did you get your source?  I downloaded a tarball from whatever was on
top of the list at sourceforge mirrors (somwhere in Gemany as I remember).

The **configuration** reports (yours and mine) agree on the version and date,
so I am assuming they are the same.

I can't find anything on my machine that indictates that **xim-**<anything> is installed.
In fact, the only things I could find with **xim** in the name were **exim4**
packages, which I do not have installed.  This one is a mystery to me.

I installed **libxpm-dev,** ran a **make clean**, re-ran the **configure**,
then did a **make** (no arguments), and the **make** succeeded.   Try that.

Instead of running **make clean**,  sometimes I remove the source directory
completely and re-extract the source directory from the tar file.

---

### Post by tonyr on 2006-06-08
OK, about the **xim** thing: **xim** is an older **[COLOR="Red"]I[/COLOR]nput [COLOR="Red"]M[/COLOR]ethod**
superceded by **SC[COLOR="Red"]IM[/COLOR]** these days.  The source may not have made allowances
for that.  See [this]("http://www.scim-im.org/wiki/faq/general/why_xim_apps_does_not_work") article.

I don't understand the ramifications at all, but the appearance of the word **locale** in
you **configuration** report leads me to believe there is somthing about **Input Method** 
and your geographical region (linux-wise) that is confusing to the build process.

---

### Post by roderikk on 2006-06-08
> **tonyr]Where did you get your source?  I downloaded a tarball from whatever was on
top of the list at sourceforge mirrors (somwhere in Gemany as I remember).[/QUOTE]

Yes, me too, can't remember where exactly.. .was a while ago.

> I installed **libxpm-dev,** ran a **make clean**, re-ran the **configure**,
then did a **make** (no arguments), and the **make** succeeded.   Try that.

Instead of running **make clean**,  sometimes I remove the source directory
completely and re-extract the source directory from the tar file.

That did the job! I did a checkinstall so with this I created my first deb file. That wasn't too difficult :-\"   said:**
> this wiki[/URL], I get an error saying:

```
urxvt: "depth": unknown or malformed option.
urxvt: "32": malformed option.
rxvt-unicode (urxvt) v7.7 - released: 2006-02-21
options: perl,styles,combining,blink,iso14755,encodin[...]
```

It says in the manual:

[QUOTE]First of all, transparency isn’t officially supported in rxvt-unicode,
       so you are mostly on your own. Do not bug the author about it (but you
       may bug everybody else). Also, if you can’t get it working consider it
       a rite of passage: ... and you failed.

And I don't want to fail... :-). Could it still have something to do with me missing something during the make phase? It did give a lót of messages after I entered make. I got xgl/compiz running and transparency is all succesfull. So again, I haven't got a clue what I am doing, does anybody do? :-)

---

### Post by tonyr on 2006-06-08
I don't know about your errors.  I didn't get them.  Try **urxvt -h** and see what it says.

---

### Post by roderikk on 2006-06-08
[QUOTE=tonyr]I don't know about your errors.  I didn't get them.  Try **urxvt -h** and see what it says.[/QUOTE]

Hm, I tried reading the manual. It says there are 4 options to make it transparent:

> Here are four ways to get transparency. Do read the manpage and option
       descriptions for the programs mentioned and rxvt-unicode. Really, do
       it!

       1. Use inheritPixmap:

          Esetroot wallpaper.jpg
          urxvt -ip -tint red -sh 40

       That works. If you think it doesn’t, you lack transparency and tinting
       support, or you are unable to read.

       2. Use a simple pixmap and emulate pseudo-transparency. This enables
       you to use effects other than tinting and shading: Just
       shade/tint/whatever your picture with gimp or any other tool:
 convert wallpaper.jpg -blur 20x20 -modulate 30 background.xpm
          urxvt -pixmap background.xpm -pe automove-background

       That works. If you think it doesn’t, you lack XPM and Perl support, or
       you are unable to read.

       3. Use an ARGB visual:

          urxvt -depth 32 -fg grey90 -bg rgba:0000/0000/4444/cccc

       This requires XFT support, and the support of your X-server. If that
       doesn’t work for you, blame Xorg and Keith Packard. ARGB visuals aren’t
       there yet, no matter what they claim. Rxvt-Unicode contains the necces&#8208;
       sary bugfixes and workarounds for Xft and Xlib to make it work, but
       that doesn’t mean that your WM has the required kludges in place.

       4. Use xcompmgr and let it do the job:

         xprop -frame -f _NET_WM_WINDOW_OPACITY 32c \
               -set _NET_WM_WINDOW_OPACITY 0xc0000000

       Then click on a window you want to make transparent. Replace 0xc0000000
       by other values to change the degree of opacity. If it doesn’t work and
       your server crashes, you got to keep the pieces.

But from what I understand only the third option gives the transparent shell without making the text transparrent... Apparently I am missing XFT support? How can I get that...? :-)

PS As long as you all keep answering, I keep asking :-P  (I tried looking it up myself but don't know what to look for...)

---

### Post by tonyr on 2006-06-08
Learning about compiling and building is one thing.  Using the result is something else.  I
could help do the first part.  Now it's up to you.  Search the forums.  Use Google.  At 
this point that's all I can do, too.

---

### Post by gadgetgirl on 2006-06-11
Make sure you installed libxft-dev since the -depth parameter will not be in the compiled urxvt otherwise.

---

