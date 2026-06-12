---
title: "installing GNU scientific library 1.14"
date: 2010-09-03
forum: General Help
---

### Post by ubun_tut on 2010-09-03
how do i install GSL 1.14? i have downloaded the tar file from [ftp://ftp.gnu.org/gnu/gsl/](ftp://ftp.gnu.org/gnu/gsl/) and it is now sitting in my Download folder. i do not really understand the instructions in the 'install' text file that came with it.

i tried the synaptic package manager, but the version in there is not updated.

---

### Post by sikander3786 on 2010-09-03
At first always try to install software from repositories.

If not then try to download a .deb package from trusted websites like [http://packages.ubuntu.com](http://packages.ubuntu.com)

If you want to install libgsl 1.13 in lucid,

```

sudo apt-get install libgsl0-dev

```

And if 1.14, manually download it from the link below, I don't know how to add the maverick repository for libgsl on lucid.

[http://packages.ubuntu.com/search?keywords=libgsl0](http://packages.ubuntu.com/search?keywords=libgsl0)

[COLOR="Red"]Edit:[/COLOR] If you still want to stick with the downloaded file, extract it and it should have a readme file containing the installation instructions.

---

### Post by ubun_tut on 2010-09-03
yes, there is an 'install' file with installation instructions:

```


Installation Instructions
=========================

GSL follows the standard GNU installation procedure.  To compile GSL
you will need an ANSI C-compiler.  After unpacking the distribution
the Makefiles can be prepared using the configure command,

  ./configure

You can then build the library by typing,

  make

Both static and shared versions of the libraries will be compiled by
default.  Compilation of shared libraries can be turned off by
specifying the `--disable-shared' option to `configure', e.g.
  
  ./configure --disable-shared

If you encounter problems building the library try using the above
option, because some platforms do not support shared libraries.  If
you change any compilation options you will need to remove any
existing compiled files with,

  make clean

before running "make" again, so the new settings take effect.

For notes about problems with specific platforms and compilers see the
next section of this file (below).

An extensive test suite is available.  After compiling the library
with "make", it can be invoked with "make check" at the top level.
The test output should be directed to a file rather than a terminal,
with the command,

   make check > log 2>&1

to allow any errors to be examined in detail.  By default, only test
failures are shown.  To see the complete output, set the environment
variable GSL_TEST_VERBOSE=1.  Use "make -k check" to continue running
the remaining tests in the event of failures.

If you run the tests and get some failures, please see the notes on
platform specific problems below.  If you find failures that are not
mentioned, please report them to bug-gsl@gnu.org.

The library can be installed using the command,

  make install

The default installation directory prefix is /usr/local.  Installing
in this directory will require root privileges on most systems (use
"su" or "sudo").

The installation directory can be changed with the --prefix option to
configure.  Consult the "Further Information" section below for
instructions on installing the library in another location or changing
other default compilation options.

When building from source, GNU packages are compiled with debugging
symbols enabled by default (CFLAGS="-g -O2").  It's part of the
philosophy that anyone should be able to examine any program on the
system.

```

the gsl folder is now in my Downloads folder. do i simply cd into that folder, then type "./configure", then "make", then "make install"?

i am using hardy by the way. thanks

---

### Post by sikander3786 on 2010-09-03
> **ubun_tut said:**
> yes, there is an 'install' file with installation instructions:

the gsl folder is now in my Downloads folder. do i simply cd into that folder, then type "./configure", then "make", then "make install"?

i am using hardy by the way. thanks

Yes those three commands should install the package.

---

### Post by ubun_tut on 2010-09-04
i did "./configure" and "make", but had to add sudo to "make install", otherwise it returned errors. now, i have quite a number of new files in my /usr/local/lib, with endings like .a, .la, .so, .0 and so on. hope this is correct.

---

### Post by naragam on 2013-01-16
Hi all,

Can somebody help me getting the gsl *.h files so that I can compile some research software that needs a bunch of include files like gsl_rng.h? I've so far tried installing packages like gsl-bin and libgslxx-dev, but I don't see the source files or include files anywhere on my system. What am I missing and what should I install to get the *.h files from gsl? 

TiA, Nash

---

