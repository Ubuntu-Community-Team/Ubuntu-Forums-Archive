---
title: "make-install"
date: 2010-02-19
forum: General Help
---

### Post by 26venger on 2010-02-19
i need help installing a source package.

im trying to install a proxy scanner program called yaph.
here are the instructions

Unpack the .tar.gz file, enter to the source directory
and type :
----------------------------------------------
./confugure
make
make install
----------------------------------------------
that's it    ;)

note:
*** you should be root to "make install".

here are the files in the directory

```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91#  ls
acinclude.m4  config.h         configure.in     Makefile.am    stamp-h.in
aclocal.m4    config.h.in      configure.in.in  Makefile.dist  subdirs
admin         config.log       COPYING          Makefile.in    TODO
AUTHORS       config.status    INSTALL          README         **yaph**
ChangeLog     configure        libtool          special.m4.in  yaph.kdevprj
config.cache  configure.files  Makefile         stamp-h

```

i ran ./configure but it only put the files in alphabetical order. i think yaph is the source directory so i changed into that directory.
here is the output 

```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91/yaph# ls
content_utils.c  globals.h   log.o        Makefile.in  threads.o
definitions.h    includes.h  main.c       tcp_utils.c  yaph.conf
docs             init.c      Makefile     tcp_utils.o  yaph.h
functions.h      log.c       Makefile.am  threads.c

```

then i ran ./configure
```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91/yaph# ./configure
bash: ./configure: No such file or directory

```

after that i ran make 

```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91/yaph# make
gcc -DHAVE_CONFIG_H -I. -I. -I..     -O2   -c init.c
init.c: In function ‘init_options’:
init.c:203: error: label at end of compound statement
make: *** [init.o] Error 1

```

then make install 
```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91/yaph# make install
gcc -DHAVE_CONFIG_H -I. -I. -I..     -O2   -c init.c
init.c: In function ‘init_options’:
init.c:203: error: label at end of compound statement
make: *** [init.o] Error 1

```

it obviously didnt install it so what am i supposed to do?

any help would be greatly appreciated

---

### Post by Tibuda on 2010-02-19
this is what you should do in a terminal as your normal user not root:
```
cd /home/slyco/Desktop/yaph-0.91
./configure
make
sudo make install
```
only "make install" should run as root, so we prefix it with "sudo".

---

### Post by n0dix on 2010-02-19
if you look there are not configure and Makefile in yaph directory, only in /home/slyco/Desktop/yaph-0.91. 
You try to run the make and make-install command in the above directory?

---

### Post by argos3016 on 2010-02-19
make clean
and configure , make , make install

if doesn't work, uncompress again.

---

### Post by 26venger on 2010-02-19
ok i did wat u guys said heres the output 

```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91# ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... (cached) gcc
checking whether the C compiler (gcc   ) works... yes
checking whether the C compiler (gcc   ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking whether  supports -frepo... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking how to recognise dependant libraries... (cached) pass_all
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for Cygwin environment... (cached) no
checking for mingw32 environment... (cached) no
loading cache ./config.cache within ltconfig
checking whether -lc should be explicitly linked in... (cached) yes
checking for objdir... .libs
checking for gcc option to produce PIC...  -fPIC -DPIC
checking if gcc PIC flag  -fPIC -DPIC works... (cached) yes
checking if gcc static flag -static works... (cached) yes
finding the maximum length of command line arguments... (cached) 73729
checking if gcc supports -c -o file.o... (cached) yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
creating libtool
loading cache ./config.cache
checking for object suffix... (cached) o
checking for executable suffix... (cached) no
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for extra includes... no
checking for extra libs... no
checking if yaph should be compiled... yes
creating ./config.status
fast creating ./Makefile
fast creating yaph/Makefile
fast creating yaph/docs/Makefile
can't open ./yaph/docs/Makefile.in: No such file or directory
fast creating yaph/docs/en/Makefile
can't open ./yaph/docs/en/Makefile.in: No such file or directory
creating config.h
config.h is unchanged

```

```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91# make
make  all-recursive
make[1]: Entering directory `/home/slyco/Desktop/yaph-0.91'
Making all in yaph
make[2]: Entering directory `/home/slyco/Desktop/yaph-0.91/yaph'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -O2   -c init.c
init.c: In function ‘init_options’:
init.c:203: error: label at end of compound statement
make[2]: *** [init.o] Error 1
make[2]: Leaving directory `/home/slyco/Desktop/yaph-0.91/yaph'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/slyco/Desktop/yaph-0.91'
make: *** [all-recursive-am] Error 2

```

```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91# sudo make install
Making install in yaph
make[1]: Entering directory `/home/slyco/Desktop/yaph-0.91/yaph'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -O2   -c init.c
init.c: In function ‘init_options’:
init.c:203: error: label at end of compound statement
make[1]: *** [init.o] Error 1
make[1]: Leaving directory `/home/slyco/Desktop/yaph-0.91/yaph'
make: *** [install-recursive] Error 1
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91# sudo make install
Making install in yaph
make[1]: Entering directory `/home/slyco/Desktop/yaph-0.91/yaph'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -O2   -c init.c
init.c: In function ‘init_options’:
init.c:203: error: label at end of compound statement
make[1]: *** [init.o] Error 1
make[1]: Leaving directory `/home/slyco/Desktop/yaph-0.91/yaph'
make: *** [install-recursive] Error 1

```

i dont understand why it says [B]make: *** [install-recursive] Error 1

please help
[/B]

---

### Post by 26venger on 2010-02-19
is it posible i need to change file permissions? pleaze look at this image.

i think there is an image anyway

---

### Post by n0dix on 2010-02-19
instead of use the su session, try to use sudo.
for change the owner do:
```
sudo chown username:username -R *
```
And try again

---

### Post by 26venger on 2010-02-19
hmm.... still no luck.

should i do a chmod +x on those files in the picture i posted that have a padlock on them?

---

### Post by n0dix on 2010-02-19
post the ls -la output. But i don't think this is the error.
Try to download the package again.

---

### Post by 26venger on 2010-02-19
```
slyco@slyco-desktop:~/Desktop/yaph-0.91$ ls -la
total 748
drwxrwxrwx  4 slyco slyco   4096 2010-02-19 18:26 .
drwxr-xr-x 12 slyco slyco   4096 2010-02-19 18:09 ..
-rw-rw-r--  1 slyco slyco 161251 2003-02-08 23:37 acinclude.m4
-rw-rw-r--  1 slyco slyco 164688 2003-02-08 23:37 aclocal.m4
drwxr-xr-x  2 slyco slyco   4096 2003-02-08 23:37 admin
-rw-rw-r--  1 slyco slyco    187 2003-02-08 23:56 AUTHORS
-rw-rw-r--  1 slyco slyco    120 2003-02-08 23:55 ChangeLog
-rw-r--r--  1 slyco slyco   2780 2010-02-19 17:10 config.cache
-rw-r--r--  1 slyco slyco    321 2010-02-19 17:10 config.h
-rw-rw-r--  1 slyco slyco    246 2003-02-08 23:37 config.h.in
-rw-r--r--  1 slyco slyco   2832 2010-02-19 18:26 config.log
-rwxr-xr-x  1 root  root    6647 2010-02-19 18:26 config.status
-rwxrwxr-x  1 slyco slyco 107810 2003-02-08 23:37 configure
-rw-rw-r--  1 slyco slyco     16 2003-02-08 23:37 configure.files
-rw-rw-r--  1 slyco slyco   3152 2003-02-08 23:37 configure.in
-rw-r--r--  1 slyco slyco   3040 2003-02-08 23:37 configure.in.in
-rw-rw-r--  1 slyco slyco  15131 2003-02-08 23:37 COPYING
-rw-rw-r--  1 slyco slyco    398 2003-02-09 15:35 INSTALL
-rwxr-xr-x  1 root  root  163796 2010-02-19 18:26 libtool
-rw-r--r--  1 root  root   16478 2010-02-19 18:26 Makefile
-rw-r--r--  1 slyco slyco   1067 2003-02-09 00:02 Makefile.am
-rw-r--r--  1 slyco slyco    449 2001-11-02 08:42 Makefile.dist
-rw-rw-r--  1 slyco slyco  16566 2003-02-09 15:44 Makefile.in
-rw-r--r--  1 slyco slyco   4727 2003-02-09 15:36 README
-rw-r--r--  1 slyco slyco   3047 2002-01-14 09:14 special.m4.in
-rw-r--r--  1 slyco slyco     10 2010-02-19 18:26 stamp-h
-rw-rw-r--  1 slyco slyco      0 2003-02-08 23:37 stamp-h.in
-rw-rw-r--  1 slyco slyco      5 2003-02-08 23:37 subdirs
-rw-rw-r--  1 slyco slyco    148 2003-02-08 23:53 TODO
drwxrwxrwx  3 slyco slyco   4096 2010-02-19 18:26 yaph
-rw-rw-r--  1 slyco slyco   2573 2003-02-09 15:44 yaph.kdevprj
slyco@slyco-desktop:~/Desktop/yaph-0.91$ 

```

thats the output of ls -la

---

### Post by n0dix on 2010-02-19
you still have files with the wrong owner. 
Run the command to change the owner. For example, Makefile.

---

### Post by 26venger on 2010-02-19
oh sorry, i wasnt sure how to run the chown command 
would i do this:

```
sudo chown slyco:build -R /home/slyco/Desktop/yaph-0.91

```

---

### Post by n0dix on 2010-02-19
> **26venger said:**
> oh sorry, i wasnt sure how to run the chown command 
would i do this:

```
sudo chown slyco:build -R /home/slyco/Desktop/yaph-0.91

```

No, 
```
sudo chown slyco:slyco -R /home/slyco/Desktop/yaph-0.91
```

---

### Post by 26venger on 2010-02-19
```
root@slyco-desktop:/home/slyco/Desktop/yaph-0.91# ls -la
total 748
drwxrwxrwx  4 slyco slyco   4096 2010-02-19 18:57 .
drwxr-xr-x 12 slyco slyco   4096 2010-02-19 18:09 ..
-rw-rw-r--  1 slyco slyco 161251 2003-02-08 23:37 acinclude.m4
-rw-rw-r--  1 slyco slyco 164688 2003-02-08 23:37 aclocal.m4
drwxr-xr-x  2 slyco slyco   4096 2003-02-08 23:37 admin
-rw-rw-r--  1 slyco slyco    187 2003-02-08 23:56 AUTHORS
-rw-rw-r--  1 slyco slyco    120 2003-02-08 23:55 ChangeLog
-rw-r--r--  1 slyco slyco   2780 2010-02-19 17:10 config.cache
-rw-r--r--  1 slyco slyco    321 2010-02-19 17:10 config.h
-rw-rw-r--  1 slyco slyco    246 2003-02-08 23:37 config.h.in
-rw-r--r--  1 slyco slyco   2832 2010-02-19 18:57 config.log
-rwxr-xr-x  1 slyco slyco   6647 2010-02-19 18:57 config.status
-rwxrwxr-x  1 slyco slyco 107810 2003-02-08 23:37 configure
-rw-rw-r--  1 slyco slyco     16 2003-02-08 23:37 configure.files
-rw-rw-r--  1 slyco slyco   3152 2003-02-08 23:37 configure.in
-rw-r--r--  1 slyco slyco   3040 2003-02-08 23:37 configure.in.in
-rw-rw-r--  1 slyco slyco  15131 2003-02-08 23:37 COPYING
-rw-rw-r--  1 slyco slyco    398 2003-02-09 15:35 INSTALL
-rwxr-xr-x  1 slyco slyco 163796 2010-02-19 18:57 libtool
-rw-r--r--  1 slyco slyco  16478 2010-02-19 18:57 Makefile
-rw-r--r--  1 slyco slyco   1067 2003-02-09 00:02 Makefile.am
-rw-r--r--  1 slyco slyco    449 2001-11-02 08:42 Makefile.dist
-rw-rw-r--  1 slyco slyco  16566 2003-02-09 15:44 Makefile.in
-rw-r--r--  1 slyco slyco   4727 2003-02-09 15:36 README
-rw-r--r--  1 slyco slyco   3047 2002-01-14 09:14 special.m4.in
-rw-r--r--  1 slyco slyco     10 2010-02-19 18:57 stamp-h
-rw-rw-r--  1 slyco slyco      0 2003-02-08 23:37 stamp-h.in
-rw-rw-r--  1 slyco slyco      5 2003-02-08 23:37 subdirs
-rw-rw-r--  1 slyco slyco    148 2003-02-08 23:53 TODO
drwxrwxrwx  3 slyco slyco   4096 2010-02-19 18:57 yaph
-rw-rw-r--  1 slyco slyco   2573 2003-02-09 15:44 yaph.kdevprj

```

the command didnt do anything

---

### Post by n0dix on 2010-02-19
If you try to run the make and make-install and they don't work. Try download again the package.

---

### Post by n0dix on 2010-02-19
Dude i think, i find the problem look this link:[http://en.allexperts.com/q/Unix-Linux-OS-1064/2008/5/configure-error-1.htm](http://en.allexperts.com/q/Unix-Linux-OS-1064/2008/5/configure-error-1.htm)

If you need help, don't doubt in asking.

---

### Post by 26venger on 2010-02-19
[n0dix]("http://ubuntuforums.org/member.php?u=226577"), thank you so much. that worked and it installed!!!!!!!!!!!!!!!

thankz for ur help and thankz for being patient

---

