---
title: "problem installing ez-ipudate for dynamic ip web hosting"
date: 2011-08-17
forum: General Help
---

### Post by tetsu7 on 2011-08-17
trying to use this program [http://www.ez-ipupdate.com/](http://www.ez-ipupdate.com/) to work with my dynamic ip address so i can host a small website on my ubuntu 11.04 machine with [https://web.easydns.com/](https://web.easydns.com/) following is the install instructions and after that is the results of the first two commands: './configure' and then 'make'
which results in the error at the bottom. im not sure what this means or how to fix it. any suggestions? the products website has no info.


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
     documentation.ez-ipupdate-3.0.11b7

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.



~/ez-ipupdate-3.0.11b7$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for a BSD compatible install... /usr/bin/install -c
checking return type of signal handlers... (cached) void
checking for gethostbyname... (cached) yes
checking for connect... (cached) yes
checking for socket... (cached) yes
checking for strdup... (cached) yes
checking for getopt_long... (cached) yes
checking for gethostbyaddr... (cached) yes
checking for getservbyname... (cached) yes
checking for inet_addr... (cached) yes
checking for inet_ntoa... (cached) yes
checking for snprintf... (cached) yes
checking for vfprintf... (cached) yes
checking for stat... (cached) yes
checking for vsprintf... (cached) yes
checking for vsnprintf... (cached) yes
checking for strerror... (cached) yes
checking for strftime... (cached) yes
checking for wait... (cached) yes
checking for waitpid... (cached) yes
checking for getpid... (cached) yes
checking for fork... (cached) yes
checking for vfork... (cached) yes
checking for getuid... (cached) yes
checking for geteuid... (cached) yes
checking for setuid... (cached) yes
checking for seteuid... (cached) yes
checking for getgid... (cached) yes
checking for getegid... (cached) yes
checking for setgid... (cached) yes
checking for setegid... (cached) yes
checking for inet_aton... (cached) yes
checking for herror... (cached) yes
checking for arpa/inet.h... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for signal.h... (cached) yes
checking for syslog.h... (cached) yes
checking for pwd.h... (cached) yes
checking for stdarg.h... (cached) yes
checking for grp.h... (cached) yes
checking for errno.h... (cached) yes
checking for sys/sockio.h... (cached) no
checking for sys/wait.h... (cached) yes
checking for getopt.h... (cached) yes
checking for unistd.h... (cached) yes
checking for netinet/in.h... (cached) yes
checking for netdb.h... (cached) yes
checking for sys/socket.h... (cached) yes
checking for sys_errlist in -lc... (cached) yes
checking for getopt... (cached) yes
checking for getpass... (cached) yes
checking host system type... i686-pc-linux-gnu
checking for user supplied default service... no
configure: warning: not setting default service
checking whether user wants debugging support... no
checking whether user wants to dissable MD5 support... no
creating ./config.status
creating Makefile
creating config.h
config.h is unchanged
boahancocksvagina@mscserver:~/ez-ipupdate-3.0.11b7$ make
gcc  -g -O2  -o ez-ipupdate  ez-ipupdate.o conf_file.o md5.o cache_file.o pid_file.o  
/usr/bin/ld: errno: TLS definition in /lib/i386-linux-gnu/libc.so.6 section .tbss mismatches non-TLS reference in conf_file.o
/lib/i386-linux-gnu/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [ez-ipupdate] Error 1

---

### Post by gordintoronto on 2011-08-17
The program is 9 years old. I don't know what a "TLS definition" is, but it seems likely that the program depends on a much older version of gcc than what you get with Ubuntu.

Another option would be to try to use the binary from the web site.

There are other programs you could try. Sorry, I can't remember names off the top of my head.

---

### Post by Cb750rider on 2011-10-26
I had a similar TLS error when compiling an older package. In my case the error was related to the errno function. I had to add #include <errno.h> to the source file, filename.c. I renamed the corresponding object file so that it would not be skipped during make, and recompiled. It looks like the old way of doing errno was to declare an int errno, but later the errno.h header was added to the c libraries, and that is what gcc wants to use. I know this is different from your error, but you may be able to find a similar outdated bit of code in the source file that is causing your error. Good Luck.

-Lee

---

