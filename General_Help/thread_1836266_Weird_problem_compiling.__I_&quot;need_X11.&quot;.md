---
title: "Weird problem compiling.  I &quot;need X11.&quot;"
date: 2011-08-30
forum: General Help
---

### Post by ninjaaron on 2011-08-30
[i]Originally titled **Weird problem compiling.  I "need X11."**
[edit] This problem probably had nothing to do with X11, but rather that I was trying to compile code that was 10+ years old.  If anyone needs to compile BasiliskII, there is are detailed instructions that worked for me [here]("http://emaculation.com/doku.php/compiling_sheepshaver_basilisk").  This program used to be packaged for Ubuntu, but it's gone now.  I may try to host a PPA for Oneiric, but I wouldn't hold your breath.
[/i]

Hi.  I'm trying to compile the [BasiliskII tarball](http://basilisk.cebix.net/downloads/BasiliskII_src_31052001.tar.gz) from [their website](http://basilisk.cebix.net/).

When I try to run the configure script ([FONT="Courier New"]./configure[/FONT]), it says this:
```
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking whether make sets ${MAKE}... yes
checking for a BSD compatible install... /usr/bin/install -c
checking for mon... no
configure: warning: Could not find mon, ignoring --with-mon.
checking for sem_init in -lposix4... no
checking for X... no
[COLOR="Red"]configure: error: You need X11 to run Basilisk II.[/COLOR]
```

I can assure you that I have X11.  I also tried to get that other stuff it said I didn't have.  I got mon, and I have no idea what it is, but it apparently has a daemon (yikes!), and did an [FONT="Courier New"]apt-cache search[/FONT] for sem_init and lposix4, and I didn't get anything back on either one.  Anyway, the real problem seems to be that I supposedly don't have X11.  Pretty sure I do, as I'm writing this in firefox.  Is it searching for it in the wrong directory, since Ubuntu put's all it's X crap in weird places?  What do I do?

[edit] Had a look at the configure script.  There were a lot of variables defined as variables defined as variables.  I'm confused, kinda like before except the same.

---

### Post by ninjaaron on 2011-08-30
Ok, I ran the "--help" for the script.

I found a couple of tags:

```
 --x-includes=DIR        X include files are in DIR
  --x-libraries=DIR       X library files are in DIR

```

I Feel like I ought to use these tags, but I don't know what the locations are in Ubuntu.  I'm kinda a newb at compiling in Ubuntu.  I can compile stuff in other distros cause everything is where it's supposed to be, so the scripts work without this nonsense.

---

### Post by ninjaaron on 2011-08-30
Ok, I installed [FONT="Courier New"]xorg-dev[/FONT], and the config script finished.

However, now [FONT="Courier New"]make[/FONT] is spewing errors left and right.  I think this still has to do with the config.   There were a lot of options that didn't get checked.  I think I need more dev stuff. Here was the final output from the configure script

```
XFree86 DGA support .............. : yes
XFree86 VidMode support .......... : yes
fbdev DGA support ................ : no
Enable video on SEGV signals ..... : yes
ESD sound support ................ : no
GTK user interface ............... : no
mon debugger support ............. : no
Running m68k code natively ....... : no
Floating-Point emulation core .... : i386 optimized core
Assembly optimizations ........... : i386
Addressing mode .................. : direct
```

And if anyone is terribly interested, here's the output from "make"...

```
c++ -I../include -I. -I../uae_cpu -DHAVE_CONFIG_H  -DOS_linux -DCPU_i386 -DDIRECT_ADDRESSING -DREGPARAM="__attribute__((regparm(3)))" -DX86_ASSEMBLY -DUNALIGNED_PROFITABLE -DOPTIMIZED_FLAGS -DFPU_X86 -D_REENTRANT -DDATADIR=\"/usr/local/share/BasiliskII\" -O2 -fomit-frame-pointer -c ../main.cpp -o obj/main.o
c++ -I../include -I. -I../uae_cpu -DHAVE_CONFIG_H  -DOS_linux -DCPU_i386 -DDIRECT_ADDRESSING -DREGPARAM="__attribute__((regparm(3)))" -DX86_ASSEMBLY -DUNALIGNED_PROFITABLE -DOPTIMIZED_FLAGS -DFPU_X86 -D_REENTRANT -DDATADIR=\"/usr/local/share/BasiliskII\" -O2 -fomit-frame-pointer -c main_unix.cpp -o obj/main_unix.o
In file included from main_unix.cpp:58:0:
/usr/include/X11/extensions/xf86dga.h:9:2: warning: #warning "xf86dga.h is obsolete and may be removed in the future."
/usr/include/X11/extensions/xf86dga.h:10:2: warning: #warning "include <X11/extensions/Xxf86dga.h> instead."
main_unix.cpp: In function ‘int main(int, char**)’:
main_unix.cpp:385:40: warning: format not a string literal and no format arguments
c++ -I../include -I. -I../uae_cpu -DHAVE_CONFIG_H  -DOS_linux -DCPU_i386 -DDIRECT_ADDRESSING -DREGPARAM="__attribute__((regparm(3)))" -DX86_ASSEMBLY -DUNALIGNED_PROFITABLE -DOPTIMIZED_FLAGS -DFPU_X86 -D_REENTRANT -DDATADIR=\"/usr/local/share/BasiliskII\" -O2 -fomit-frame-pointer -c ../prefs.cpp -o obj/prefs.o
c++ -I../include -I. -I../uae_cpu -DHAVE_CONFIG_H  -DOS_linux -DCPU_i386 -DDIRECT_ADDRESSING -DREGPARAM="__attribute__((regparm(3)))" -DX86_ASSEMBLY -DUNALIGNED_PROFITABLE -DOPTIMIZED_FLAGS -DFPU_X86 -D_REENTRANT -DDATADIR=\"/usr/local/share/BasiliskII\" -O2 -fomit-frame-pointer -c ../prefs_items.cpp -o obj/prefs_items.o
c++ -I../include -I. -I../uae_cpu -DHAVE_CONFIG_H  -DOS_linux -DCPU_i386 -DDIRECT_ADDRESSING -DREGPARAM="__attribute__((regparm(3)))" -DX86_ASSEMBLY -DUNALIGNED_PROFITABLE -DOPTIMIZED_FLAGS -DFPU_X86 -D_REENTRANT -DDATADIR=\"/usr/local/share/BasiliskII\" -O2 -fomit-frame-pointer -c prefs_unix.cpp -o obj/prefs_unix.o
c++ -I../include -I. -I../uae_cpu -DHAVE_CONFIG_H  -DOS_linux -DCPU_i386 -DDIRECT_ADDRESSING -DREGPARAM="__attribute__((regparm(3)))" -DX86_ASSEMBLY -DUNALIGNED_PROFITABLE -DOPTIMIZED_FLAGS -DFPU_X86 -D_REENTRANT -DDATADIR=\"/usr/local/share/BasiliskII\" -O2 -fomit-frame-pointer -c sys_unix.cpp -o obj/sys_unix.o
sys_unix.cpp:36:16: error: ‘_llseek’ has not been declared
sys_unix.cpp:36:31: error: ‘fd’ has not been declared
sys_unix.cpp:36:42: error: ‘hi’ has not been declared
sys_unix.cpp:36:53: error: ‘lo’ has not been declared
sys_unix.cpp:36:67: error: ‘res’ has not been declared
sys_unix.cpp:36:78: error: ‘wh’ has not been declared
sys_unix.cpp:36:81: error: expected constructor, destructor, or type conversion before ‘;’ token
sys_unix.cpp: In function ‘void* Sys_open(const char*, bool)’:
sys_unix.cpp:299:41: error: ‘_llseek’ was not declared in this scope
sys_unix.cpp: In function ‘size_t Sys_read(void*, void*, loff_t, size_t)’:
sys_unix.cpp:380:52: error: ‘_llseek’ was not declared in this scope
sys_unix.cpp: In function ‘size_t Sys_write(void*, void*, loff_t, size_t)’:
sys_unix.cpp:406:52: error: ‘_llseek’ was not declared in this scope
sys_unix.cpp: In function ‘bool SysIsDiskInserted(void*)’:
sys_unix.cpp:565:45: error: ‘INT_MAX’ was not declared in this scope
sys_unix.cpp: In function ‘void* Sys_open(const char*, bool)’:
sys_unix.cpp:305:23: warning: ignoring return value of ‘ssize_t read(int, void*, size_t)’, declared with attribute warn_unused_result
make: *** [obj/sys_unix.o] Error 1
ninjaaron@CQ61:~/Downloads/BasiliskII-0.9/src/Unix$ make install
c++ -I../include -I. -I../uae_cpu -DHAVE_CONFIG_H  -DOS_linux -DCPU_i386 -DDIRECT_ADDRESSING -DREGPARAM="__attribute__((regparm(3)))" -DX86_ASSEMBLY -DUNALIGNED_PROFITABLE -DOPTIMIZED_FLAGS -DFPU_X86 -D_REENTRANT -DDATADIR=\"/usr/local/share/BasiliskII\" -O2 -fomit-frame-pointer -c sys_unix.cpp -o obj/sys_unix.o
sys_unix.cpp:36:16: error: ‘_llseek’ has not been declared
sys_unix.cpp:36:31: error: ‘fd’ has not been declared
sys_unix.cpp:36:42: error: ‘hi’ has not been declared
sys_unix.cpp:36:53: error: ‘lo’ has not been declared
sys_unix.cpp:36:67: error: ‘res’ has not been declared
sys_unix.cpp:36:78: error: ‘wh’ has not been declared
sys_unix.cpp:36:81: error: expected constructor, destructor, or type conversion before ‘;’ token
sys_unix.cpp: In function ‘void* Sys_open(const char*, bool)’:
sys_unix.cpp:299:41: error: ‘_llseek’ was not declared in this scope
sys_unix.cpp: In function ‘size_t Sys_read(void*, void*, loff_t, size_t)’:
sys_unix.cpp:380:52: error: ‘_llseek’ was not declared in this scope
sys_unix.cpp: In function ‘size_t Sys_write(void*, void*, loff_t, size_t)’:
sys_unix.cpp:406:52: error: ‘_llseek’ was not declared in this scope
sys_unix.cpp: In function ‘bool SysIsDiskInserted(void*)’:
sys_unix.cpp:565:45: error: ‘INT_MAX’ was not declared in this scope
sys_unix.cpp: In function ‘void* Sys_open(const char*, bool)’:
sys_unix.cpp:305:23: warning: ignoring return value of ‘ssize_t read(int, void*, size_t)’, declared with attribute warn_unused_result
make: *** [obj/sys_unix.o] Error 1
```

I'm going to keep trying, but I'm not optimistic.  I'm just following my guts, and my guts don't know anything about compiling from source in Ubuntu.

---

### Post by ninjaaron on 2011-08-30
Yeah, I just installed about a million gtk related dev packages.  No luck.

I'm stuck.

HELP!

---

### Post by Bachstelze on 2011-08-30
This code is over ten years old for some files, I think it needs a lot of work to make it compile on a current system.

---

### Post by ninjaaron on 2011-08-30
> **Bachstelze said:**
> This code is over ten years old for some files, I think it needs a lot of work to make it compile on a current system.

damn.  I think I saw a natty bzr branch... maybe I can try that.

---

### Post by sum1nil on 2011-08-30
Did you try installing 'xlibs-dev'?

---

### Post by ninjaaron on 2011-08-30
alright,  I found [this site]("http://emaculation.com/doku.php/compiling_sheepshaver_basilisk") with up-to-date instructions.  Never in my life have I worked so hard to build a stinking package.

There is a version of this software that runs flawlessly in WINE...  Don't ask me why I decided it would be better to run it natively...


> **sum1nil said:**
> Did you try installing 'xlibs-dev'?

Yes. The X thing is more or less solved.  Now I've "upgraded" to fighting with ancient code. I changed the thread title, but sometime it takes a while for the change to kick in on the with the forum software, it seems like.

---

### Post by ninjaaron on 2011-08-30
Ok.  The instructions from the new site worked.  I have a binary.  It runs.  Now I just have to figure out how to use the program. :p

Marking as solved and adding the site that works to the OP.

Not that anyone will ever get anything out of this thread if they search for it and find it.

---

