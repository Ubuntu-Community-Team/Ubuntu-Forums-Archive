---
title: "Compiling error"
date: 2009-12-17
forum: General Help
---

### Post by mainegeek on 2009-12-17
Hello everyone--
 
OK, I've got a frustrating problem on a production Ubuntu Jaunty server. Something I've been working on for a few days now with little avail.
 
The server runs Zabbix and a few other misc tasks. Zabbix is its primary task though.
 
I have Zabbix 1.6 installed and I want to upgrade to Zabbix 1.8. I did the initial Zabbix install from source months ago.
 
So, I unzipped the tar/gzip source for Zabbix 1.8 on the system and ran the 'configure' command. It ran through fine but I realised I forgot a parameter in to the configure (--with-jabber) so I reran configure but this time it dies saying 'C compiler cannot create executables'. So I tried again but this time I took out the parameter for jabber.... same thing!
 
Next step I blew away the source directory and re-extracted it again from the compressed file--same thing!
 
Next, I created a simple C program
```

#include <stdio.h>
int main(void)
{
    printf("Hello World\n");
    return 0;
}

```
 
And compiled it
```

gcc -o hello hello.c

```
 
It works! Great.... but now I'm really wondering what my issue is
 
Here is the config.log
```

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin
configure:1914: checking for a BSD-compatible install
configure:1970: result: /usr/bin/install -c
configure:1981: checking whether build environment is sane
configure:2024: result: yes
configure:2052: checking for a thread-safe mkdir -p
configure:2091: result: /bin/mkdir -p
configure:2104: checking for gawk
configure:2134: result: no
configure:2104: checking for mawk
configure:2120: found /usr/bin/mawk
configure:2131: result: mawk
configure:2142: checking whether make sets $(MAKE)
configure:2167: result: no
configure:2352: Configuring
configure:2355: checking whether make sets $(MAKE)
configure:2380: result: no
configure:2395: checking build system type
configure:2413: result: i686-pc-linux-gnu
configure:2435: checking host system type
configure:2450: result: i686-pc-linux-gnu
configure:2521: checking for gcc
configure:2537: found /usr/bin/gcc
configure:2548: result: gcc
configure:2786: checking for C compiler version
configure:2793: gcc --version >&5
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
configure:2796: $? = 0
configure:2803: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4)
configure:2806: $? = 0
configure:2813: gcc -V >&5
gcc: '-V' option must have argument
configure:2816: $? = 1
configure:2839: checking for C compiler default output file name
configure:2866: gcc -O2 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions   conftest.c  >&5
**/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o: In function `_start':**
**/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'**
collect2: ld returned 1 exit status
configure:2869: $? = 1
configure:2907: result:
configure: failed program was:
**configure:2914: error: C compiler cannot create executables**
See `config.log' for more details.
 
ac_cv_build=i686-pc-linux-gnu
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=set
ac_cv_env_CFLAGS_value='-O2 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions'
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_IKSEMEL_CFLAGS_set=
ac_cv_env_IKSEMEL_CFLAGS_value=
ac_cv_env_IKSEMEL_LIBS_set=
ac_cv_env_IKSEMEL_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnu
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=no
 
ACLOCAL='${SHELL} /home/service/zabbix-1.8/missing --run aclocal-1.10'
AGENT_FALSE=''
AGENT_TRUE=''
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/service/zabbix-1.8/missing --run tar'
ARCH=''
AUTOCONF='${SHELL} /home/service/zabbix-1.8/missing --run autoconf'
AUTOHEADER='${SHELL} /home/service/zabbix-1.8/missing --run autoheader'
AUTOMAKE='${SHELL} /home/service/zabbix-1.8/missing --run automake-1.10'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CFLAGS='-O2 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions'
CPP=''
CPPFLAGS=''
CYGPATH_W='echo'
DB_CPPFLAGS=''
DB_LDFLAGS=''
DB_LIBS=''
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GREP=''
ICONV_CFLAGS=''
ICONV_LDFLAGS=''
IKSEMEL_CFLAGS=''
IKSEMEL_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
IODBC_CFLAGS=''
IODBC_LDFLAGS=''
IODBC_LIBS=''
JABBER_CPPFLAGS=''
JABBER_FALSE=''
JABBER_LDFLAGS=''
JABBER_LIBS=''
JABBER_TRUE=''
LDAP_CPPFLAGS=''
LDAP_LDFLAGS=''
LDFLAGS=''
LIBCURL_CFLAGS=''
LIBCURL_LDFLAGS=''
LIBCURL_LIBS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/service/zabbix-1.8/missing --run makeinfo'
MYSQL_CFLAGS=''
MYSQL_CONFIG=''
MYSQL_LDFLAGS=''
MYSQL_LIBS=''
MYSQL_VERSION=''
OBJEXT=''
ODBC_CFLAGS=''
ODBC_LDFLAGS=''
ODBC_LIBS=''
OPENIPMI_CPPFLAGS=''
OPENIPMOPENIPMIFLAGS=''
ORACLE_CPPFLAGS=''
ORACLE_LDFLAGS=''
ORACLE_LIBS=''
ORACLE_OCI_CFLAGS=''
ORACLE_OCI_LDFLAGS=''
ORACLE_OCI_LIBS=''
ORACLE_OCI_VERSION=''
PACKAGE='zabbix'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PG_CONFIG=''
PKG_CONFIG=''
POSTGRESQL_CPPFLAGS=''
POSTGRESQL_LDFLAGS=''
POSTGRESQL_VERSION=''
PROXY_FALSE=''
PROXY_LDFLAGS=''
PROXY_LIBS=''
PROXY_TRUE=''
RANLIB=''
SERVER_FALSE=''
SERVER_LDFLAGS=''
SERVER_LIBS=''
SERVER_TRUE=''
SET_MAKE='MAKE=make'
SHELL='/bin/bash'
SNMP_CFLAGS=''
SNMP_CPPFLAGS=''
SNMP_LDFLAGS=''
SNMP_LIBS=''
SQLITE3_CPPFLAGS=''
SQLITE3_LDFLAGS=''
SQLITE3_VERSION=''
SSH2_CFLAGS=''
SSH2_LDFLAGS=''
SSH2_LIBS=''
STRIP=''
UNIXODBC_CFLAGS=''
UNIXODBC_LDFLAGS=''
UNIXODBC_LIBS=''
VERSION='1.8'
WITH_ODBC_FALSE=''
WITH_ODBC_TRUE=''
_libcurl_config=''
_libnetsnmp_config=''
_libodbc_config=''
ac_ct_CC='gcc'
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include=''
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /home/service/zabbix-1.8/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''
 
configure: exit 77

```
 
Remember, Zabbix compiled once. It feels like the compiler parameters may be wrong but I don't know enough about it.
 
I'm trying to avoid having to rebuild the box (since it is production). I'm also thinking of trying 'apt-get dist-upgrade' but I'm afraid that may cause more issues.
 
I have even tried removing gcc / headers / build-essential packages (apt-get purge / apt-get autoremove) and even downgrading gcc; same thing
 
Before anyone says I'm supposed to use sudo I want you to know that I am running as root (sudo -s).
 
I have been using linux for years; I've recompiled kernels and various software packages. I've ran into snags during that time but never something like this that has not changed regardless what I do.
 
Anybody have any ideas?

---

### Post by pbrane on 2009-12-17
it looks like ld failed **collect2: ld returned 1 exit status**. Are you sure you have binutils installed correctly? Did config.log have any additional clues?

Also I'm not sure what this is doing:
[B]configure:2813: gcc -V >&5
gcc: '-V' option must have argument
[/B]
the -V option should have a version as it's argument, telling gcc which version to use in case you have more than one version installed. This may not be an issue though.

But the main thing is that ld can't find the 'main' function definition. 

> 
I have even tried removing gcc / headers / build-essential packages (apt-get purge / apt-get autoremove) and even downgrading gcc; same thing


I assume you have re-installed this stuff? If you can you might try running aptitude to see if any packages are broken.

---

### Post by mainegeek on 2009-12-17
pbrane, thansk for the quick response.
 
Yup, I have binutils
```

root@bu1emmc:/usr/bin# dpkg -l | grep binutils
ii  binutils                                  2.19.1-0ubuntu3                   The GNU assembler, linker and binary utiliti
ii  binutils-static                           2.19.1-0ubuntu3                   statically linked binutils tools

```
 
Yes I reverted back to gcc 4.3.3 since 3.4 did not resolve
 
> 
Also I'm not sure what this is doing:
[B]configure:2813: gcc -V >&5
gcc: '-V' option must have argument
[/B]
the -V option should have a version as it's argument, telling gcc which version to use in case you have more than one version installed. This may not be an issue though.

 
I believe that is just part of the configure command just attempting to learn the system.  Zabbix can be compiled on many platforms so I think it is just a general test
 
> 
Did config.log have any additional clues?

 
These are the lines that jump out at me
```

**/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o: In function `_start':**
**/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'**
collect2: ld returned 1 exit status
configure:2869: $? = 1
configure:2907: result:
configure: failed program was:
**configure:2914: error: C compiler cannot create executables**

```
 
I don't understand why crt1.o would complain about **main** being missing.
 
I even thought crt1.o was corrupt at one point because of the ld following
```

[EMAIL="root@bu1emmc:/usr/bin"][COLOR=black]root@bu1emmc:/usr/bin[/COLOR][/EMAIL]# ld /usr/lib/crt1.o
/usr/lib/crt1.o: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:109: undefined reference to `__libc_csu_fini'
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:110: undefined reference to `__libc_csu_init'
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:119: undefined reference to `__libc_start_main'

```
 
But one google post said this is expected behavior from ld against crt1.o since it needs to be linked to something.
 
I also re-installed glibc to be safe....
 
> If you can you might try running aptitude to see if any packages are broken
 
Nothing appears to be broken
 
Thanks!

---

### Post by pbrane on 2009-12-17
Where ld is actually failing is when conftest.c is being linked. Noting these lines:
[B]configure:2839: checking for C compiler default output file name
configure:2866: gcc -O2 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions   conftest.c  >&5
[/B]

This is from a configure file that I ran on my machine:
[B]configure:3307: checking for C compiler default output file name
configure:3329: gcc    conftest.c  >&5
configure:3333: $? = 0
configure:3370: result: a.out
configure:3386: checking whether the C compiler works
configure:3395: ./a.out
configure:3399: $? = 0
configure:3414: result: yes[/B]

It's not Zabbix but the configure script is doing about the same thing. I wonder if the parameters to the conftest compile have anything to do with it? I have not had this happen before. It's very strange. If I come across anything I'll post again.

One more thing, if you have autogen.sh in the Zabbix source you might try a **make distclean** (although that probably won't even run) and then run ./autogen.sh to build the configure script for your machine. I have had issues with source that came with a configure script for some other machine. You can even copy the system autogen.sh to that directory, I think, if it doesn't exist. Seems like I have done that before. Or maybe all you need to do is run autoconf.

---

### Post by mainegeek on 2009-12-17
Yes I noticed that as well.
 
It's really weird because it did compile at one point.
 
> 
One more thing, if you have autogen.sh in the Zabbix source you might try a **make distclean** (although that probably won't even run) and then run ./autogen.sh to build the configure script for your machine. I have had issues with source that came with a configure script for some other machine. You can even copy the system autogen.sh to that directory, I think, if it doesn't exist. Seems like I have done that before. Or maybe all you need to do is run autoconf.

 
Yeah, no autogen.sh script unfortunately.... I tried autoconf per your suggestion and still when I configure I get the same message
 
Thanks for your responses

---

### Post by pbrane on 2009-12-17
You're welcome. right now I'm out of ideas. I suppose it is possible that Zabbix 1.8 is broken for later versions of gcc.

Although, I would be tempted to edit the configure script and remove those parameters from the conftest build line. After all coonfigure just wants the gcc default program name, which is usually a.out on linux.

---

### Post by mainegeek on 2009-12-17
> **pbrane said:**
> You're welcome. right now I'm out of ideas. I suppose it is possible that Zabbix 1.8 is broken for later versions of gcc.

Although, I would be tempted to edit the configure script and remove those parameters from the conftest build line. After all coonfigure just wants the gcc default program name, which is usually a.out on linux.

Yeah I started to look at the configure code and try to get it to skip conftest but I didn't make any changes yet.  My bash scripting is ok but isn't really strong so I'm not completely sure what it is doing at a few points.  I'll take a look at it further tomorrow and report back.  

Perhaps, skipping the conftest will work or at the least get me to another (maybe more useful) error.

Thanks again

---

### Post by pbrane on 2009-12-17
It just dawned on me that you might try deleting **.cache** in the home directory of the user that you used to compile the source. root, I believe in your case. I had to do this once when something really odd was happening while trying to build an app from source.

---

### Post by mainegeek on 2009-12-17
> **pbrane said:**
> It just dawned on me that you might try deleting **.cache** in the home directory of the user that you used to compile the source. root, I believe in your case. I had to do this once when something really odd was happening while trying to build an app from source.
 
Hmmm interesting... I couldn't find .cache. Is this used by gcc?
```

find / -name .cache

```
It finds nothing
 
I REALLY want to get this working so I decided to do some remote work.
 
I hacked away at configure by commenting out some of the tests and manually set thr output file variable to a.out. This got me farther but its still tripping up in a few checks... I think I'm almost there; if it compiles is a different story though
 
I'll let you know...
 
Thanks again

---

### Post by pbrane on 2009-12-17
I think I steered you srong with that last post. I *thought* I had to delete that directory at one point. But when I look at it now there is nothing related to gcc or autom4te. I must have been thinking about the autom4te.cache directory in the source dir. But since you have deleted the source dir and untarred/unzipped a new copy....

---

### Post by mainegeek on 2009-12-17
> 
config.status: creating man/Makefile
config.status: creating include/config.h
config.status: executing depfiles commands
 
Configuration:
Detected OS: linux-gnu
Install path: /usr/local
Compilation arch: linux
Compiler: gcc
Compiler flags: -g -O2 -I/usr/include/mysql -DBIG_JOINS=1 -fno-strict-aliasing -DUNIV_LINUX -I/usr/local/include -I/usr/lib/perl/5.10/CORE -I. -I/usr/include
Enable server: yes
With database: MySQL
WEB Monitoring via: cURL
Native Jabber: no
SNMP: net-snmp
IPMI: no
Linker flags: -L/usr/lib/mysql -lcurl -lidn -lssl -lcrypto -llber -lldap -lrt -lgssapi_krb5 -lgssapi_krb5 -lssl -lcrypto -lz -L/usr/lib -lnetsnmp -lcrypto -L/usr/lib -lnetsnmp -lcrypto
Libraries: -lm -lresolv -lmysqlclient -lcurl -lnetsnmp
Enable proxy: no
Enable agent: no
LDAP support: no
IPv6 support: no
***********************************************************
* Now run 'make install' *
* *
* Thank you for using ZABBIX! *
* <[http://www.zabbix.com](http://www.zabbix.com)> *
***********************************************************

 
[\\:D/]("file://\\:D/")
 
No errors so far.... hopefully its not broken

---

### Post by pbrane on 2009-12-17
LOL. So the solution was to bypass the conftest.c compile?

---

### Post by mainegeek on 2009-12-17
Yes, mostly! In all I commented out three small sections and had to manually set a variable.
 
After that it was all dependacy problems that apt-get install solved.
 
When this started I removed/reinstalled SO many packages trying to resolve that a few were still missing.
 
Again, hopefully the final result is a working copy.
 
I wish I understood what actually happened though.... configure ran fine earlier this week but I wanted to add jabber support. Unfortunately after installing the required jabber libraries it wouldn't compile again. This time I decided not to include jabber support! :)
 
I still think it is a compiler option; possible env var that changed somehow.
 
Anyone who googles for a fix and ends up here... sorry guys/gals; nothing definitive just a bit a hacking....
 
Thanks again pbrane

---

### Post by falconindy on 2009-12-17
Had this problem recently on a Slackware VM install. Turned out to be an issue with trying to compile the wrong architecture (i686 v x86_64).

---

### Post by pbrane on 2009-12-17
Again, you're welcome. I didn't really do much though. YOu figured it out. But like you I am curious about that error. I did find out that it can occur if a parameter or compiler option is wrong ( misspelled, or otherwise incorrect ). Maybe someone will have a definitive answer.

---

### Post by mainegeek on 2009-12-17
> **falconindy said:**
> Had this problem recently on a Slackware VM install. Turned out to be an issue with trying to compile the wrong architecture (i686 v x86_64).
 
I'm not looking for any special architecture... just i386. The server isn't 64bit. I know there is an enviroment var that you can use to control this but that's all the I know.
 
Got a bit more insight as to where I should look?
 
I'd be willing to make a copy of my configure, restore the original, and try again to see if this is the case. I still haven't run make.
 
Thanks

---

### Post by falconindy on 2009-12-17
Seems to me like there's some conflicting lines in the output of ./configure from your first post:

```
configure:2395: checking build system type
configure:2413: result: i686-pc-linux-gnu
configure:2435: checking host system type
configure:2450: result: i686-pc-linux-gnu
...
Target: i486-linux-gnu
Configured with: ../src/configure -v [...] --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
```
You might try overriding the --build, --host, and --target flags to be i686 rather than i486.

---

### Post by mainegeek on 2009-12-17
> **falconindy said:**
> Seems to me like there's some conflicting lines in the output of ./configure from your first post:

```
configure:2395: checking build system type
configure:2413: result: i686-pc-linux-gnu
configure:2435: checking host system type
configure:2450: result: i686-pc-linux-gnu
...
Target: i486-linux-gnu
Configured with: ../src/configure -v [...] --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
```You might try overriding the --build, --host, and --target flags to be i686 rather than i486.

Excellent!  Thanks falconindy... I totally missed the architecture mismatch.  Hopefully that is it.  Although it might work, I'm not feeling good about having to modify the configure script.

I'll look into this further tomorrow and report back

Thanks

---

### Post by mainegeek on 2009-12-18
Great advice falconindy! It worked!
 
I restored the original configure script and ran it with the following parameters
> ./configure **--build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu** --enable-server --with-mysql --with-net-snmp --with-libcurl

 
So manually overriding it works.... but I wonder why by default it wants to be built for a i486. I'm not THAT interested though... AND, I won't be forgetting this one ANY TIME soon.
 
Thank you both for all your comments and advice!
 
Maybe there is hope for future googlers afterall! :)

---

### Post by pbrane on 2009-12-18
Interesting that you had to force the architecture. I would think that particular configure script is broken, because configuring the build for your machine is what it's supposed to do!

---

