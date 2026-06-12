---
title: "Problems Installing Tarballs"
date: 2011-10-06
forum: General Help
---

### Post by kjstearn on 2011-10-06
Hi everyone,

I am new to linux and new to the forum so I would apperciate any help you can give me. I am trying to install some software I need for my research project ( can be found here: [http://www.mina.ubc.ca/qcadesigner_downloads](http://www.mina.ubc.ca/qcadesigner_downloads)). The problem is after I unpack it, I can not get it to configure:

```
root@kyle-PC:~# cd /home/kyle/src/QCADesigner-2.0.3
root@kyle-PC:~/src/QCADesigner-2.0.3# ./configure.in
bash: ./configure.in: Permission denied

```

I have been trying to figure out what is wrong and from what I can figure it out it may have to do with my fstab file listing the drive as noexec or something. I am not really sure what to do about this.

here is my /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6e271e79-bcbb-4916-a3a5-0d6bb763c533 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c0e4fc20-d7fc-491d-8690-4f9f29c1e157 none            swap    sw              0       0
```

Can anyone walk me though what I need to do?

Thanks

Kyle

---

### Post by blueridgedog on 2011-10-06
Is the .configure.in executable?

What is the output of:

```
ls -al /home/kyle/src/QCADesigner-2.0.3
```

---

### Post by smurphy_it on 2011-10-06
No that's the /proc folder only which is no exec.  Once you extracted the files / directories, you are trying to run it as your user I'm assuming, but we don't know if that file has execute permission rights on it or not.

Can you do a chmod a+x /home/kyle/src/QCADesigner-2.0.3/config.in ?
Also, perhaps you could do a listing of that directory and files for us to ensure the ownerships are right.

```
ls -ld /home/kyle/src/QCADesigner-2.0.3/
ls -la /home/kyle/src/QCADesigner-2.0.3/

```

Post back those results if you don't mind, thanks.

---

### Post by kjstearn on 2011-10-06
> **blueridgedog said:**
> Is the .configure.in executable?

What is the output of:

```
ls -al /home/kyle/src/QCADesigner-2.0.3
```

the ouput was:

```
ls -al /home/kyle/src/QCADesigner-2.0.3
total 224
drwxr-xr-x 7  502 users  4096 2005-07-28 02:01 .
drwxr-xr-x 3 kyle kyle   4096 2011-10-06 10:39 ..
-rw-r--r-- 1  502 users   261 2005-05-29 03:53 AUTHORS
-rwxr-xr-x 1  502 users  1782 2005-07-17 02:10 autogen.sh
-rw-r--r-- 1  502 users  1522 2005-05-29 03:53 ChangeLog
-rw-r--r-- 1  502 users  2993 2005-07-27 20:47 configure.in
-rw-r--r-- 1  502 users 17992 2003-08-25 16:50 COPYING
-rw-r--r-- 1  502 users   313 2005-05-29 03:53 CurrentVerChangeLog
-rw-r--r-- 1  502 users   113 2003-09-03 12:39 .cvsignore
drwxr-xr-x 3  502 users  4096 2005-07-28 02:01 docs
drwxr-xr-x 2  502 users  4096 2005-07-28 02:01 file_formats
-rw-r--r-- 1  502 users   323 2005-06-24 00:08 graph_dialog.desktop.in
-rw-r--r-- 1  502 users  7831 2003-08-25 16:50 INSTALL
-rw-r--r-- 1  502 users   862 2005-07-27 23:27 Makefile.am
-rw-r--r-- 1  502 users     0 2003-08-25 16:50 NEWS
drwxr-xr-x 2  502 users  4096 2005-07-28 02:01 pixmaps
drwxr-xr-x 2  502 users  4096 2005-07-28 02:01 po
-rw-r--r-- 1  502 users   307 2005-06-24 00:08 QCADesigner.desktop.in
-rw-r--r-- 1  502 users  2277 2005-07-27 20:47 QCADesigner.spec.in
-rw-r--r-- 1  502 users  8173 2005-07-27 23:26 QCADesigner-win32-gtk.iss.in
-rw-r--r-- 1  502 users  7270 2005-07-27 23:26 QCADesigner-win32.iss.in
-rw-r--r-- 1  502 users   705 2004-03-25 22:15 README
-rw-r--r-- 1  502 users  1687 2004-03-25 22:15 README.win32.txt
-rw-r--r-- 1  502 users 95900 2005-05-29 01:24 sample.qca
drwxr-xr-x 4  502 users  4096 2005-07-28 02:01 src
-rw-r--r-- 1  502 users  4813 2005-07-27 20:47 TODO

```

---

### Post by kjstearn on 2011-10-06
> **smurphy_it said:**
> No that's the /proc folder only which is no exec.  Once you extracted the files / directories, you are trying to run it as your user I'm assuming, but we don't know if that file has execute permission rights on it or not.

Can you do a chmod a+x /home/kyle/src/QCADesigner-2.0.3/config.in ?
Also, perhaps you could do a listing of that directory and files for us to ensure the ownerships are right.

```
ls -ld /home/kyle/src/QCADesigner-2.0.3/
ls -la /home/kyle/src/QCADesigner-2.0.3/

```

Post back those results if you don't mind, thanks.

the results of these where:

```
kyle@kyle-PC:~$ ls -ld /home/kyle/src/QCADesigner-2.0.3/
drwxr-xr-x 7 502 users 4096 2005-07-28 02:01 /home/kyle/src/QCADesigner-2.0.3/
kyle@kyle-PC:~$ ls -la /home/kyle/src/QCADesigner-2.0.3/
total 224
drwxr-xr-x 7  502 users  4096 2005-07-28 02:01 .
drwxr-xr-x 3 kyle kyle   4096 2011-10-06 10:39 ..
-rw-r--r-- 1  502 users   261 2005-05-29 03:53 AUTHORS
-rwxr-xr-x 1  502 users  1782 2005-07-17 02:10 autogen.sh
-rw-r--r-- 1  502 users  1522 2005-05-29 03:53 ChangeLog
-rw-r--r-- 1  502 users  2993 2005-07-27 20:47 configure.in
-rw-r--r-- 1  502 users 17992 2003-08-25 16:50 COPYING
-rw-r--r-- 1  502 users   313 2005-05-29 03:53 CurrentVerChangeLog
-rw-r--r-- 1  502 users   113 2003-09-03 12:39 .cvsignore
drwxr-xr-x 3  502 users  4096 2005-07-28 02:01 docs
drwxr-xr-x 2  502 users  4096 2005-07-28 02:01 file_formats
-rw-r--r-- 1  502 users   323 2005-06-24 00:08 graph_dialog.desktop.in
-rw-r--r-- 1  502 users  7831 2003-08-25 16:50 INSTALL
-rw-r--r-- 1  502 users   862 2005-07-27 23:27 Makefile.am
-rw-r--r-- 1  502 users     0 2003-08-25 16:50 NEWS
drwxr-xr-x 2  502 users  4096 2005-07-28 02:01 pixmaps
drwxr-xr-x 2  502 users  4096 2005-07-28 02:01 po
-rw-r--r-- 1  502 users   307 2005-06-24 00:08 QCADesigner.desktop.in
-rw-r--r-- 1  502 users  2277 2005-07-27 20:47 QCADesigner.spec.in
-rw-r--r-- 1  502 users  8173 2005-07-27 23:26 QCADesigner-win32-gtk.iss.in
-rw-r--r-- 1  502 users  7270 2005-07-27 23:26 QCADesigner-win32.iss.in
-rw-r--r-- 1  502 users   705 2004-03-25 22:15 README
-rw-r--r-- 1  502 users  1687 2004-03-25 22:15 README.win32.txt
-rw-r--r-- 1  502 users 95900 2005-05-29 01:24 sample.qca
drwxr-xr-x 4  502 users  4096 2005-07-28 02:01 src
-rw-r--r-- 1  502 users  4813 2005-07-27 20:47 TODO

```

---

### Post by MG&amp;TL on 2011-10-06
What does the README say?

---

### Post by kjstearn on 2011-10-06
> **MG&TL said:**
> What does the README say?

QCADesigner README Notes
============================

If you would like to run QCADesigner from the source tree,
that is, you do not want to perform "make install", you
may do so by switching to the src/ subdirectory and
running ./QCADesigner .

If you would like to install QCADesigner to a path other
than the default you can run configure with the --prefix
option and specify the path. For example if you are
configuring QCADesigner for the first time, you can run:

./autogen.sh --prefix=<Your path>
make
make install

"ls <Your path>" should show a "bin" and "share" directory
that contain all the files that QCADesigner has installed.
You can then use the script provided above to run
QCADesigner.

Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Compilers and Options
=====================

   Some systems require unusual options for compilation or linking that
the `configure' script does not know about.  You can give `configure'
initial values for variables by setting them in the environment.  Using
a Bourne-compatible shell, you can do that on the command line like
this:
     CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure

Or on systems that have the `env' program, you can do it like this:
     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not supports the `VPATH'
variable, you have to compile the package for one architecture at a time
in the source code directory.  After you have installed the package for
one architecture, use `make distclean' before reconfiguring for another
architecture.

Installation Names
==================

   By default, `make install' will install the package's files in
`/usr/local/bin', `/usr/local/man', etc.  You can specify an
installation prefix other than `/usr/local' by giving `configure' the
option `--prefix=PATH'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
give `configure' the option `--exec-prefix=PATH', the package will use
PATH as the prefix for installing programs and libraries.
Documentation and other data files will still use the regular prefix.

   In addition, if you use an unusual directory layout you can give
options like `--bindir=PATH' to specify different values for particular
kinds of files.  Run `configure --help' for a list of the directories
you can set and what kinds of files go in them.

   If the package supports it, you can cause programs to be installed
with an extra prefix or suffix on their names by giving `configure' the
option `--program-prefix=PREFIX' or `--program-suffix=SUFFIX'.

Optional Features
=================

   Some packages pay attention to `--enable-FEATURE' options to
`configure', where FEATURE indicates an optional part of the package.
They may also pay attention to `--with-PACKAGE' options, where PACKAGE
is something like `gnu-as' or `x' (for the X Window System).  The
`README' should mention any `--enable-' and `--with-' options that the
package recognizes.

   For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.

Specifying the System Type
==========================

   There may be some features `configure' can not figure out
automatically, but needs to determine by the type of host the package
will run on.  Usually `configure' can figure that out, but if it prints
a message saying it can not guess the host type, give it the
`--host=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name with three fields:
     CPU-COMPANY-SYSTEM

See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the host type.

   If you are building compiler tools for cross-compiling, you can also
use the `--target=TYPE' option to select the type of system they will
produce code for and the `--build=TYPE' option to select the type of
system on which you are compiling the package.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Operation Controls
==================

   `configure' recognizes the following options to control how it
operates.

`--cache-file=FILE'
     Use and save the results of the tests in FILE instead of
     `./config.cache'.  Set FILE to `/dev/null' to disable caching, for
     debugging `configure'.

`--help'
     Print a summary of the options to `configure', and exit.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.  To
     suppress all normal output, redirect it to `/dev/null' (any error
     messages will still be shown).

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`--version'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`configure' also accepts some other, not widely useful, options.

---

### Post by haqking on 2011-10-06
is there any reason why you are logged in as root ? we use [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

Root should not be enabled in Ubuntu.

in the first post you are logged in as root

later on you are not.

Why the inconsistency ?

---

### Post by kjstearn on 2011-10-06
> **kjstearn said:**
> QCADesigner README Notes
============================

If you would like to run QCADesigner from the source tree,
that is, you do not want to perform "make install", you
may do so by switching to the src/ subdirectory and
running ./QCADesigner .

If you would like to install QCADesigner to a path other
than the default you can run configure with the --prefix
option and specify the path. For example if you are
configuring QCADesigner for the first time, you can run:

./autogen.sh --prefix=<Your path>
make
make install

"ls <Your path>" should show a "bin" and "share" directory
that contain all the files that QCADesigner has installed.
You can then use the script provided above to run
QCADesigner.

Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Compilers and Options
=====================

   Some systems require unusual options for compilation or linking that
the `configure' script does not know about.  You can give `configure'
initial values for variables by setting them in the environment.  Using
a Bourne-compatible shell, you can do that on the command line like
this:
     CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure

Or on systems that have the `env' program, you can do it like this:
     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not supports the `VPATH'
variable, you have to compile the package for one architecture at a time
in the source code directory.  After you have installed the package for
one architecture, use `make distclean' before reconfiguring for another
architecture.

Installation Names
==================

   By default, `make install' will install the package's files in
`/usr/local/bin', `/usr/local/man', etc.  You can specify an
installation prefix other than `/usr/local' by giving `configure' the
option `--prefix=PATH'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
give `configure' the option `--exec-prefix=PATH', the package will use
PATH as the prefix for installing programs and libraries.
Documentation and other data files will still use the regular prefix.

   In addition, if you use an unusual directory layout you can give
options like `--bindir=PATH' to specify different values for particular
kinds of files.  Run `configure --help' for a list of the directories
you can set and what kinds of files go in them.

   If the package supports it, you can cause programs to be installed
with an extra prefix or suffix on their names by giving `configure' the
option `--program-prefix=PREFIX' or `--program-suffix=SUFFIX'.

Optional Features
=================

   Some packages pay attention to `--enable-FEATURE' options to
`configure', where FEATURE indicates an optional part of the package.
They may also pay attention to `--with-PACKAGE' options, where PACKAGE
is something like `gnu-as' or `x' (for the X Window System).  The
`README' should mention any `--enable-' and `--with-' options that the
package recognizes.

   For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.

Specifying the System Type
==========================

   There may be some features `configure' can not figure out
automatically, but needs to determine by the type of host the package
will run on.  Usually `configure' can figure that out, but if it prints
a message saying it can not guess the host type, give it the
`--host=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name with three fields:
     CPU-COMPANY-SYSTEM

See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the host type.

   If you are building compiler tools for cross-compiling, you can also
use the `--target=TYPE' option to select the type of system they will
produce code for and the `--build=TYPE' option to select the type of
system on which you are compiling the package.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Operation Controls
==================

   `configure' recognizes the following options to control how it
operates.

`--cache-file=FILE'
     Use and save the results of the tests in FILE instead of
     `./config.cache'.  Set FILE to `/dev/null' to disable caching, for
     debugging `configure'.

`--help'
     Print a summary of the options to `configure', and exit.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.  To
     suppress all normal output, redirect it to `/dev/null' (any error
     messages will still be shown).

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`--version'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`configure' also accepts some other, not widely useful, options.

I have tried following these instructions with no success

---

### Post by MG&amp;TL on 2011-10-06
And if you're not too bothered about installing, you can run it as described by cd'ing to /bin, then running the program with ./<program>

---

### Post by kjstearn on 2011-10-06
> **haqking said:**
> is there any reason why you are logged in as root ? we use [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

Root should not be enabled in Ubuntu.

in the first post you are logged in as root

later on you are not.

Why the inconsistency ?

because I was trying to use root to get access to run the config... so i logged on using sudo -s, I tried it without being logged on and got the same thing. In the second post I had new instance of terminal running where I did not log in as root

---

### Post by kjstearn on 2011-10-06
> **MG&TL said:**
> And if you're not too bothered about installing, you can run it as described by cd'ing to /bin, then running the program with ./<program>

I would like to install... I will be using this program for a few months

---

### Post by jazzon on 2011-10-06
quick and dirty method to fix (i think)

cd to /home/kyle/src/QCADesigner-2.0.3

then do [HTML]sudo chmod -R 777 ./*[/HTML]

don't recommend to get in this habit but it will force writ-ability to all sub files here.

Huge security risk if you do this anywhere else.

BE SURE IT IS DOT SLASH STAR!!  NOT JUST SLASH STAR!

This will cause all files and folders in this directory and below this directory to be world read write and executable.  Not a wise thing to do, but since the instalation folder (this one) will presumably be deleted after you install it, it will be ok.  (if deleting)

---

### Post by kjstearn on 2011-10-06
> **jazzon said:**
> quick and dirty method to fix (i think)

cd to /home/kyle/src/QCADesigner-2.0.3

then do [HTML]sudo chmod -R 777 ./*[/HTML]

don't recommend to get in this habit but it will force writ-ability to all sub files here.

Huge security risk if you do this anywhere else.

BE SURE IT IS DOT SLASH STAR!!  NOT JUST SLASH STAR!

I if I do this will I be able to install as usual?

---

### Post by jazzon on 2011-10-06
yes but i forgot a step
also change them all to you as owner (assuming your kyle)
[HTML]sudo chown -R kyle:kyle ./*[/HTML]

---

### Post by jazzon on 2011-10-06
by the way Q-CAD is available for ubuntu...you shouldnt need the tarball.  You could just 

sudo apt-get install qcad ,

 or use synaptic or whatever.

its version 2.0.5.0

---

### Post by kjstearn on 2011-10-06
> **jazzon said:**
> by the way Q-CAD is available for ubuntu...you shouldnt need the tarball.  You could just 

sudo apt-get install qcad ,

 or use synaptic or whatever.

its version 2.0.5.0

it is not the same program... I need QCADesigner... not QCAD... they do very different things

---

### Post by jazzon on 2011-10-06
sorry, should have checked that first.  Didn't realize it was different software.

---

### Post by jazzon on 2011-10-06
This is not Ubuntu specific, and is probably way out dated by now, but most of the things which are basic to linux dont change very much over time.  Being new to linux in general this might be of use to you.

[RUTE]("http://rute.2038bug.com/index.html.gz")

This book has been freely available for years, and is where i got my start.

It explains things like the <snip>
[HTML]drwxr-xr-x 7  502 users  4096 2005-07-28 02:01 .
drwxr-xr-x 3 kyle kyle   4096 2011-10-06 10:39 ..
-rw-r--r-- 1  502 users   261 2005-05-29 03:53 AUTHORS
-rwxr-xr-x 1  502 users  1782 2005-07-17 02:10 autogen.sh
[/HTML]
<snip>

-rw-r--r-- on the AUTHORS file.
(those are user permissions by the way, owner read write, group read, other read)  and how to change them (the chmod thing i showed you)  and 502 is the owner of the file (should be kyle) thats why the chown thing.

Good luck and I hope you enjoy your new computing world!

---

### Post by blueridgedog on 2011-10-06
What happens when you try and run ./autogen.sh from the directory as your normal user as directed in the file?  Can you post the error?

---

### Post by kjstearn on 2011-10-06
> **jazzon said:**
> yes but i forgot a step
also change them all to you as owner (assuming your kyle)
[HTML]sudo chown -R kyle:kyle ./*[/HTML]

So I tried those things... and now when i run the config i get this...

```
root@kyle-PC:~# cd /home/kyle/src/QCADesigner-2.0.3
root@kyle-PC:~/src/QCADesigner-2.0.3# ./configure
bash: ./configure: No such file or directory
root@kyle-PC:~/src/QCADesigner-2.0.3# ./configure.in
./configure.in: line 1: dnl: command not found
./configure.in: line 3: syntax error near unexpected token `configure.in'
./configure.in: line 3: `AC_INIT(configure.in)'

```

?

---

### Post by blueridgedog on 2011-10-06
> **kjstearn said:**
> So I tried those things... and now when i run the config i get this...

```
root@kyle-PC:~# cd /home/kyle/src/QCADesigner-2.0.3
root@kyle-PC:~/src/QCADesigner-2.0.3# ./configure
bash: ./configure: No such file or directory
root@kyle-PC:~/src/QCADesigner-2.0.3# ./configure.in
./configure.in: line 1: dnl: command not found
./configure.in: line 3: syntax error near unexpected token `configure.in'
./configure.in: line 3: `AC_INIT(configure.in)'

```

?


You are not to run ./configure.in, it should be ./autogen.sh.

---

### Post by kjstearn on 2011-10-06
> **blueridgedog said:**
> What happens when you try and run ./autogen.sh from the directory as your normal user as directed in the file?  Can you post the error?

```
kyle@kyle-PC:~$ cd /home/kyle/src/QCADesigner-2.0.3
kyle@kyle-PC:~/src/QCADesigner-2.0.3$ ./autogen.sh
+ WANT_AUTOMAKE=1.6
+ WANT_AUTOCONF_2_5=1
+ ACLOCAL_INCLUDE=
+ export WANT_AUTOMAKE
+ export WANT_AUTOCONF_2_5
+ export ACLOCAL_INCLUDE
+ set +x
+ '[' '' = '' ']'
+ aclocal
./autogen.sh: line 48: aclocal: command not found
+ automake --gnu --add-missing
./autogen.sh: line 53: automake: command not found
+ glib-gettextize -c
./autogen.sh: line 54: glib-gettextize: command not found
+ autoconf
./autogen.sh: line 55: autoconf: command not found

```

---

### Post by jazzon on 2011-10-06
Kyle,

Much of the instructions given on that page you posted are copy pasted from a generic installation notes file.  You will see many of these over time with linux, and the wording is identical.  He is right run
[HTML]./autogen.sh[/HTML] The results should be better.

---

### Post by jazzon on 2011-10-06
OK, you are missing some dependencies here.  Ubuntu is meant to be a binary distribution, so not all build dependencies ship with it.  Give me (us) a few minutes and we should be able to determine what your missing.

---

### Post by jazzon on 2011-10-06
[HTML]sudo apt-get install automake[/HTML] for starters, and retry

---

### Post by blueridgedog on 2011-10-06
Install automake then try again...you have dependencies for the compile that you need to work out (the reason people use deb packages...it is listing them for you).


```
sudo apt-get install automake
```

....edit...ok, too many cooks, but you get the idea...you have to get your build environment setup to compile the application and install it.

---

### Post by haqking on 2011-10-06
or you could download the .rpm and use alien

---

### Post by kjstearn on 2011-10-06
> **jazzon said:**
> Kyle,

Much of the instructions given on that page you posted are copy pasted from a generic installation notes file.  You will see many of these over time with linux, and the wording is identical.  He is right run
[HTML]./autogen.sh[/HTML] The results should be better.

so when i ran ./autogen.sh I get:

```
kyle@kyle-PC:~/src/QCADesigner-2.0.3$ ./autogen.sh
+ WANT_AUTOMAKE=1.6
+ WANT_AUTOCONF_2_5=1
+ ACLOCAL_INCLUDE=
+ export WANT_AUTOMAKE
+ export WANT_AUTOCONF_2_5
+ export ACLOCAL_INCLUDE
+ set +x
+ '[' '' = '' ']'
+ aclocal
./autogen.sh: line 48: aclocal: command not found
+ automake --gnu --add-missing
./autogen.sh: line 53: automake: command not found
+ glib-gettextize -c
./autogen.sh: line 54: glib-gettextize: command not found
+ autoconf
./autogen.sh: line 55: autoconf: command not found

```

Im guessing this means that I am not all set?

---

### Post by kjstearn on 2011-10-06
> **jazzon said:**
> OK, you are missing some dependencies here.  Ubuntu is meant to be a binary distribution, so not all build dependencies ship with it.  Give me (us) a few minutes and we should be able to determine what your missing.

thanks alot everyone... I really appreciate the help... take all the time you need

---

### Post by kjstearn on 2011-10-06
> **jazzon said:**
> [HTML]sudo apt-get install automake[/HTML] for starters, and retry

after running the above i tried again and got:

```
kyle@kyle-PC:~/src/QCADesigner-2.0.3$ ./autogen.sh
+ WANT_AUTOMAKE=1.6
+ WANT_AUTOCONF_2_5=1
+ ACLOCAL_INCLUDE=
+ export WANT_AUTOMAKE
+ export WANT_AUTOCONF_2_5
+ export ACLOCAL_INCLUDE
+ set +x
+ '[' '' = '' ']'
+ aclocal
configure.in:106: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autom4te: cannot create autom4te.cache: No such file or directory
aclocal: autom4te failed with exit status: 1
+ automake --gnu --add-missing
autom4te: cannot create autom4te.cache: No such file or directory
automake: autoconf failed with exit status: 1
+ glib-gettextize -c
./autogen.sh: line 54: glib-gettextize: command not found
+ autoconf
autom4te: cannot create autom4te.cache: No such file or directory

```

---

### Post by jazzon on 2011-10-06
I am still looking, but haq is probably right about that (the very fact he thought of it that fast says he knows more than I do)  You might want to try that route.  You might need to [HTML]sudo apt-get install alien[/HTML], im not sure if it comes as default.  Also I don't know how to use it myself as Ive never had to.  But it is often a solution for these types of things from what I have seen in these pages.

---

### Post by blueridgedog on 2011-10-06
As a learning experience you should note that when you try to install something, it will typically tell you the error:

```
+ aclocal
./autogen.sh: line 48: [COLOR="Red"]aclocal: command not found[/COLOR]
+ automake --gnu --add-missing
./autogen.sh: line 53: [COLOR="red"]automake: command not found[/COLOR]
+ glib-gettextize -c
./autogen.sh: line 54: [COLOR="red"]glib-gettextize: command not found[/COLOR]
+ autoconf
./autogen.sh: line 55: [COLOR="red"]autoconf: command not found[/COLOR]
```

Your job is to then seek out ways to get the libraries that you need to do the compile. At times it may take a good bit of searching to find the right package or file that installs each.  For glib-gettextize, I would search google for "glib-gettextize ubuntu package that provides"  One of the first links is to:

[http://manpages.ubuntu.com/manpages/hardy/man1/glib-gettextize.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/glib-gettextize.1.html)

That indicates that you need  libglib2.0-dev_2.16.3-1_i386 or greater, so I would then open up synaptic and search for  libglib2.0-dev.  You may hit other compile issues, but each one can be handled in turn.

---

### Post by jazzon on 2011-10-06
[HTML]sudo apt-get install libc6[/HTML]
and rerun autogen


edit:

forget that do what blue said

---

### Post by haqking on 2011-10-06
download the .rpm

```
sudo apt-get install alien
```

```
sudo alien *.rpm
```

where * is the package name

this converts the .rpm to a .deb it there is multiple .rpm then use * anyways

then once you have the .deb or .debs

```
sudo dpkg -i *.deb
```

---

### Post by blueridgedog on 2011-10-06
> **haqking said:**
> download the .rpm



Easy, true...but just think what the OP will learn if he/she sticks it out and gets their rig set for compiling software?

---

### Post by jazzon on 2011-10-06
+1 vote for blue!

---

### Post by haqking on 2011-10-06
> **blueridgedog said:**
> Easy, true...but just think what the OP will learn if he/she sticks it out and gets their rig set for compiling software?

oh dont get me wrong im totally for that and prefer that people do.

Just providing an option to get the software installed and used if the OP chooses an easy out ;-)

peace

---

### Post by blueridgedog on 2011-10-06
> **haqking said:**
> oh dont get me wrong im totally for that and prefer that people do.

I think you don't really know Linux until you have had to spend 10 hours getting something to compile, chasing down missing libraries and resolving dependencies that compound as you go further up the tree (I need version 2 of this, but it requires version 3 of that, but it requires this...on and on and on...I compiled mono from source about six months ago and it brought back some painful memories of Linux before package managers).

---

### Post by kjstearn on 2011-10-06
> **blueridgedog said:**
> Easy, true...but just think what the OP will learn if he/she sticks it out and gets their rig set for compiling software?

I don't know what an OP is but I am assuming it is a linux newb... I am going to stick it out because part of my research will involve makeing alot of changes to this simulator so I need to learn this stuff

---

### Post by haqking on 2011-10-06
> **blueridgedog said:**
> I think you don't really know Linux until you have had to spend 10 hours getting something to compile, chasing down missing libraries and resolving dependencies that compound as you go further up the tree (I need version 2 of this, but it requires version 3 of that, but it requires this...on and on and on...I compiled mono from source about six months ago and it brought back some painful memories of Linux before package managers).

oh definately i hear ya and agree.

But i have found with Ubuntu one of the reasons why people turn to it is its "ease of use", and often people are coming from a lack of control environment and often see the ability to control everything as a unnecessary complication, the OP mentioned they were new to Linux and so often these sorts of posts are followed up by a rant about why is Linux so complicated....LOL

anyways hopefully they will stick with it and get it working, feel accomplished and carry on enjoying Linux and with new found knowledge, if not there are a couple of other options for them ;-)

---

### Post by haqking on 2011-10-06
> **kjstearn said:**
> I don't know what an OP is but I am assuming it is a linux newb... I am going to stick it out because part of my research will involve makeing alot of changes to this simulator so I need to learn this stuff

OP means original post, which means your post or you ;-)

Yeah stick with it, it is a great learning experience as mentioned.

You now also know if you didnt already you can use a .rpm if you have to.

Happy compiling and good luck ;-)

---

### Post by jazzon on 2011-10-06
OP is Original Poster, and don't feel bad, we all started right where you are.

---

### Post by jazzon on 2011-10-06
How about an update?  Working yet?  Where you at what you tried etc.
(also messaged your acct here. IUm holding off bed till you  fix this or at least get a handle on it...so fill me in)

---

### Post by MG&amp;TL on 2011-10-06
Compiling from source is never easy, but it brings a big learning curve. Have fun. :)

---

### Post by kjstearn on 2011-10-06
> **jazzon said:**
> How about an update?  Working yet?  Where you at what you tried etc.
(also messaged your acct here. IUm holding off bed till you  fix this or at least get a handle on it...so fill me in)

I am not much further then I was before... I had a soccer game that I just got back from and now I have to do my homework due tomorrow so this will have to wait till then. I will make sure I give you guys an update tomorrow afternoon after I start at it again.

Thanks everyone

---

