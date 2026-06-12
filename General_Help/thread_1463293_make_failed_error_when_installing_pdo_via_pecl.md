---
title: "make failed error when installing pdo via pecl"
date: 2010-04-26
forum: General Help
---

### Post by ckankiewicz on 2010-04-26
I'm on Ubuntu 9.10 64-bit trying to install pdo and pdo_mysql, but whenever I run "sudo pecl install pdo" I get the following output:

```
downloading PDO-1.0.3.tgz ...
Starting to download PDO-1.0.3.tgz (52,613 bytes)
.............done: 52,613 bytes
12 source files, building
running: phpize
Configuring for:
PHP Api Version:         20090626
Zend Module Api No:      20090626
Zend Extension Api No:   220090626
building in /var/tmp/pear-build-root/PDO-1.0.3
running: /tmp/pear/temp/PDO/configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20090626
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking whether to enable PDO support... yes, shared
checking for ld used by cc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from cc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if cc supports -fno-rtti -fno-exceptions... no
checking for cc option to produce PIC... -fPIC
checking if cc PIC flag -fPIC works... yes
checking if cc static flag -static works... yes
checking if cc supports -c -o file.o... yes
checking whether the cc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
configure: creating ./config.status
config.status: creating config.h
running: make
/bin/bash /var/tmp/pear-build-root/PDO-1.0.3/libtool --mode=compile cc  -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/PDO/pdo.c -o pdo.lo
mkdir .libs
 cc -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/PDO/pdo.c  -fPIC -DPIC -o .libs/pdo.o
/bin/bash /var/tmp/pear-build-root/PDO-1.0.3/libtool --mode=compile cc  -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/PDO/pdo_dbh.c -o pdo_dbh.lo
 cc -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/PDO/pdo_dbh.c  -fPIC -DPIC -o .libs/pdo_dbh.o
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_stmt_instantiate’:
/tmp/pear/temp/PDO/pdo_dbh.c:410: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c:411: error: ‘zval’ has no member named ‘is_ref’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_stmt_construct’:
/tmp/pear/temp/PDO/pdo_dbh.c:435: error: ‘zend_fcall_info’ has no member named ‘object_pp’
/tmp/pear/temp/PDO/pdo_dbh.c:458: error: ‘zend_fcall_info_cache’ has no member named ‘object_pp’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘zim_PDO_setAttribute’:
/tmp/pear/temp/PDO/pdo_dbh.c:752: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘zim_PDO_getAttribute’:
/tmp/pear/temp/PDO/pdo_dbh.c:818: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_hash_methods’:
/tmp/pear/temp/PDO/pdo_dbh.c:1122: warning: assignment discards qualifiers from pointer target type
/tmp/pear/temp/PDO/pdo_dbh.c:1126: warning: assignment discards qualifiers from pointer target type
make: *** [pdo_dbh.lo] Error 1
ERROR: `make' failed
```What am I doing wrong?

---

### Post by ckankiewicz on 2010-04-27
Is anyone able to help?

---

### Post by kamil.jakubowski on 2010-05-10
I have the same problem. The problem was appeared when updated my ubuntu from 9 to 10 (php5.3 was installed).

Unfortunately I didn't find solution for this problem. There are few similar topics in internet, but anyone has solution.

---

### Post by lachild on 2010-05-19
Ok I've found the solution to our problems.  The biggest issue here is that PDO is no longer supported in PECL and has been moved to CORE.  

On that note all the PDO drivers for the respected databases have been moved into the main php5 database packages.  So when you install php5-sqlite it not only installs the basic driver it also installs the pdo driver at the same time.

Now if you are getting this error that means that you already attempted to install the outdated pecl version.   Doing that seems to corrupt your php installation and now even if you install the right package it still wont work.

To fix this you must PURGE not remove all the installed packages that start with php5 including php itself.

Once all these packages are purged reinstall the ones you deleted. 

Finally install the correct php5 database package, so for sqlite install php5-sqlite.  After which pdo-sqlite will be properly installed and ready for use.


Hope this helps,
LaChild

---

### Post by NumPy on 2010-09-03
Thank you! Saved me a bit of t/s on this issue!

---

### Post by vele on 2011-11-20
> **lachild said:**
> Ok I've found the solution to our problems.  The biggest issue here is that PDO is no longer supported in PECL and has been moved to CORE.  

On that note all the PDO drivers for the respected databases have been moved into the main php5 database packages.  So when you install php5-sqlite it not only installs the basic driver it also installs the pdo driver at the same time.

Now if you are getting this error that means that you already attempted to install the outdated pecl version.   Doing that seems to corrupt your php installation and now even if you install the right package it still wont work.

To fix this you must PURGE not remove all the installed packages that start with php5 including php itself.

Once all these packages are purged reinstall the ones you deleted. 

Finally install the correct php5 database package, so for sqlite install php5-sqlite.  After which pdo-sqlite will be properly installed and ready for use.


Hope this helps,
LaChild

thanks!
After a whole day of searching for a solution to enable curl and pdo, although i had installed them previously, i have found this, followed all steps, and now it works like a charm! 
thank you one more time ;)

---

### Post by oldos2er on 2011-11-20
Closed, necromancy.

---

