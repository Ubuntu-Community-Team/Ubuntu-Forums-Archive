---
title: "GNU build system problem with CXXFLAGS"
date: 2012-05-24
forum: General Help
---

### Post by ldt on 2012-05-24
I'm stumped with a GNU build system problem when using the CXXFLAGS macro. I have a package I'm preparing for distribution with the GNU build system which contains several executables. Most are in C but a couple are in C++. I've done similar packages before without problems. In fact I've copied from them to set up the initial files as a template for the current package. All goes well until I try to build the first C++ program. It contains both C and C++ files (not a problem in previous packages.) Programms built with the CFLAGS macro work fine. However, when using the CXXFLAGS macro, when compiling the *.c files it fails because the command line generated has ignored the include directories from the line "myprogram_CXXFLAGS = -I/dir/inc.h". No matter what I try the include file directory flags simple don't show up on the generated gcc command line.

As a test, I eliminated the *.c files from the projects and tried to just build the *.cpp files. Then I simply get the error "*** No rule to make target `myfile.cpp' even though it is definitely there.

Its worked before and I can see no difference between the configure.ac & Makefile.am files between the package that works and the one that doesn't. I'll be happy to provide the relevant files on request.

Stumped.

If there is a better forum to ask this question on I'd be glad to hear about that too.

Thanks.

---

### Post by ldt on 2012-05-25
I got it after a day and a half of serious head banging. Basically, I had two problems. First and worst, I hadn't read the autotools documentation carefully enough. Second, even after I got the autotools fixed I had a very difficult to spot misspelling.

Most of you probably already know this, but just in case anyone else is having autotools problems, here are the steps I took to get it right.

0. Read the autoconf & automake manuals. Here are a few links that I used:
   [http://sources.redhat.com/autobook/autobook/autobook_toc.html](http://sources.redhat.com/autobook/autobook/autobook_toc.html)
   [http://www.gnu.org/software/autoconf/manual/autoconf.html](http://www.gnu.org/software/autoconf/manual/autoconf.html)
   [http://www.gnu.org/software/automake/manual/html_node/index.html](http://www.gnu.org/software/automake/manual/html_node/index.html)
   [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

1. Carefully write all of the Makefile.am files to get all of the subdirs correct.
2. Run autoscan to create configuration.scan, an initial configuration.ac file
3. Edit configuration.scan macros AC_INIT, to customize the package name & package info, and add AM_INIT_AUTOMAKE, do define some special distribution files I wanted, and save it as configuration.ac.
4. Run the following series of build commands:
   aclocal
   autoconf
   autoheader
   automake --add-missing
   ./configure
   make all
   make dist

It took a few iterations of step 4. with edits to the Makefile.am flags and sources. In fact I had to read through the generated Makefiles to figure out that projects with mixed *.c and *.cpp files need to use CPPFLAGS instead of CXXFLAGS. But I finally have my distribution packages.

Thanks.

---

