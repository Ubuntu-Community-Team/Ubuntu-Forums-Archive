---
title: "Octave  and Java"
date: 2012-02-05
forum: General Help
---

### Post by ahowe42 on 2012-02-05
Hello all.

I have octave 3.2.4 on Ubuntu 11.10, and trying to install the java package from octave-forge.  I downloaded and ran the pkg installation, only to have it fail because I didn't have the JDK installed.  I installed this from synaptic package manager (ver 7~b147-2.0ubuntu0.11.10.1).  When I run the package installation again, I get the following (First of all, I don't see any error in this...):


ahowe42@Neuromancer:~$ sudo octave
[sudo] password for ahowe42: 

GNU Octave, version 3.2.4
Copyright (C) 2009 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-pc-linux-gnu".

Additional information about Octave is available at [http://www.octave.org](http://www.octave.org).

Please contribute if you find this software useful.
For more information, visit [http://www.octave.org/help-wanted.html](http://www.octave.org/help-wanted.html)

Report bugs to <bug@octave.org> (but first, please read
[http://www.octave.org/bugs.html](http://www.octave.org/bugs.html) to learn how to write a helpful report).

For information about changes from previous versions, type `news'.

warning: mark_as_command is obsolete and will be removed from a future version of Octave
octave:1> pkg install ~/Downloads/java-1.2.8.tar.gz -verbose
In file included from __java__.cc:17:0:
__java__.h:25:17: fatal error: jni.h: No such file or directory
compilation terminated.
make: *** [__java__.oct] Error 1
mkdir (/tmp/oct-H4IkYV)
untar (/home/ahowe42/Downloads/java-1.2.8.tar.gz, /tmp/oct-H4IkYV)
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for mkoctfile... mkoctfile
retrieving compile and link flags from mkoctfile
checking for F77_FUNC... yes
checking for octave... octave
checking for OCTAVE_VERSION in Octave... 3.2.4
checking for octave_config_info('canonical_host_type') in Octave... x86_64-pc-linux-gnu
checking for octave_config_info('SHLEXT') in Octave... so
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for strip... strip
checking for java... java
checking for javac... javac
checking for jar... jar
checking for Java version... 1.6.0_23
configure: creating ./config.status
config.status: creating Makeconf
 
  "$prefix" is /usr/share/octave/packages/3.2/java-1.2.8
  "$exec_prefix" is ${prefix}

octave commands will install into the following directories:
   m-files:   /usr/share/octave/3.2.4/site/m/octave-forge
   oct-files: /usr/lib/octave/3.2.4/site/oct/x86_64-pc-linux-gnu/octave-forge
   binaries:  /usr/lib/octave/3.2.4/site/exec/x86_64-pc-linux-gnu
alternatives:
   m-files:   /usr/share/octave/3.2.4/site/octave-forge-alternatives/m
   oct-files: /usr/lib/octave/3.2.4/site/octave-forge-alternatives/oct/x86_64-pc-linux-gnu

shell commands will install into the following directories:
   binaries:  ${exec_prefix}/bin
   man pages: ${datarootdir}/man
   libraries: ${exec_prefix}/lib
   headers:   ${prefix}/include

octave-forge is configured with
   octave:      octave (version 3.2.4)
   mkoctfile:	mkoctfile for Octave 4
   java:        yes

find . -name NOINSTALL -print    # shows which toolboxes won't be installed

'make' returned the following error: make: Entering directory `/tmp/oct-H4IkYV/java/src'
if [ "Xamd64X" = "XX" ]; then \
		mkoctfile -DHAVE_OCTAVE_32 -v -DJAVAPKG_BUILD -I/usr/lib/jvm/default-java/include -I/usr/lib/jvm/default-java/include/linux -o __java__.oct __java__.cc ; \
	else \
		mkoctfile -DHAVE_OCTAVE_32 -v -DJAVAPKG_BUILD -DJAVA_ARCH=\\\"amd64\\\" -DJAVA_HOME=\\\"/usr/lib/jvm/default-java\\\" -I/usr/lib/jvm/default-java/include -I/usr/lib/jvm/default-java/include/linux -o __java__.oct __java__.cc ; \
	fi
g++ -c -fPIC -I/usr/include/octave-3.2.4 -I/usr/include/octave-3.2.4/octave -I/usr/include/mpi -I/usr/include/freetype2 -O2 -g -I/usr/lib/jvm/default-java/include -I/usr/lib/jvm/default-java/include/linux -DHAVE_OCTAVE_32 -DJAVAPKG_BUILD -DJAVA_ARCH=\"amd64\" -DJAVA_HOME=\"/usr/lib/jvm/default-java\" __java__.cc -o __java__.o
make: Leaving directory `/tmp/oct-H4IkYV/java/src'
error: called from `pkg>configure_make' in file /usr/share/octave/3.2.4/m/pkg/pkg.m near line 1253, column 2
error: called from:
error:   /usr/share/octave/3.2.4/m/pkg/pkg.m at line 714, column 5
error:   /usr/share/octave/3.2.4/m/pkg/pkg.m at line 287, column 7

If anyone can give some guidance, I will be very appreciative!

Andrew

---

### Post by ahowe42 on 2012-02-09
Made some progress on this (kind of).  The package installer now seems to have no error finding the jdk while installing the java package.  If I try to use the inputdlg function that is part of the java package, I get this:


 a = inputdlg({'a';'b'},'title',1,{'42';'1024'},'off');
error: java_invoke: /usr/lib/jvm/java-1.6.0-openjdk/jre/lib/amd64/client/libjvm.so: failed to load: /usr/lib/jvm/java-1.6.0-openjdk/jre/lib/amd64/client/libjvm.so: cannot open shared object file: No such file or directory
error: called from:
error:   /usr/local/share/octave/packages/java-1.2.8/inputdlg.m at line 98, column 15

The problem is that it can't find the libjvm.so file, which is because it's not in a "client" directory.  I can find it, but it's either in the /usr/lib/jvm/*JDK VERSION/jre/lib/amd64/server folder or in the /usr/lib/jvm/*JDK VERSION/jre/lib/amd64/cacao folder.

Why would the octave java package be expecting this directory structure with the client folder that doesn't exist?  I have jdk 1.6, 1.7, 6, 7, default (all with amd64) all in the /usr/lib/jvm folder, if it helps...

Thanks for any help anyone can give.

Andrew

---

### Post by Cavsfan on 2012-02-09
You could try the links in my signature. One tests your version of java and if it's not up to date, will provide a link to download the file.
You will want the file that ends win ".bin" and not ".rpm".
The other will provide step by step instructions for installing the file you just downloaded.

It says to remove the old version first. If you have a 32 bit machine use the left side of that page.
If you have a 64 bit machine, use the right side. I have used this many times with great success.

---

### Post by ahowe42 on 2012-02-09
Ok, so I removed the different java installations, then verified the /usr/lib/jvm folder was gone.  I then reinstalled (from apt-get) the latest version for ubuntu - openjdk-6-jre, openjdk-6-jdk, and icedtea6-plugin.  No errors during installation here.

Then I removed the java package from octave (run as root) and reinstalled it with no errors.

Same error with running java_invoke - it can't find libjvm.so still because it's in a .../cacao/ directory and not .../client/ directory.  Everything else is the same.

In fact, now I can no longer run java from the terminal.  What environment variable to I need to set to do this?

Andrew

---

### Post by Cavsfan on 2012-02-09
> **ahowe42 said:**
> Ok, so I removed the different java installations, then verified the /usr/lib/jvm folder was gone.  I then reinstalled (from apt-get) the latest version for ubuntu - openjdk-6-jre, openjdk-6-jdk, and icedtea6-plugin.  No errors during installation here.

Then I removed the java package from octave (run as root) and reinstalled it with no errors.

Same error with running java_invoke - it can't find libjvm.so still because it's in a .../cacao/ directory and not .../client/ directory.  Everything else is the same.

In fact, now I can no longer run java from the terminal.  What environment variable to I need to set to do this?

Andrew
If the links I provided didn't help, I have no idea. I don't use octave.

---

### Post by ahowe42 on 2012-02-10
Do you have suggestions for fixing my java installation now?  Before I removed and reinstalled java per your links, I could run java from the terminal, but now I get

ahowe42@Neuromancer:~$ java
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

even though I installed it correctly (openjdk-6-jre, openjdk-6-jdk, and icedtea6-plugin no errors):


ahowe42@Neuromancer:/usr/lib/jvm$ dir
default-java  java-1.6.0-openjdk  java-6-openjdk

Thanks.

Oh, and if anyone else has the same problem with octave, my solution which seems to have worked was to create a symlink:

sudo ln -s -v '/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server' '/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/client'


Andrew

---

### Post by Cavsfan on 2012-02-10
So, are you saying you got it fixed with the symlink?
When I entered "java" in terminal I get the help, usage etc.
The instructions in my sig. do not install openjdk-6-jre, openjdk-6-jdk, and icedtea6-plugin.

As a matter of fact, they say to remove the icedtea6-plugin via Ubuntu Software Center.

I don't use octave, but the method works for java as I have used it almost a dozen times with success.

---

