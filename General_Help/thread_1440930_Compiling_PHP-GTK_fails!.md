---
title: "Compiling PHP-GTK fails!"
date: 2010-03-28
forum: General Help
---

### Post by Grozzy on 2010-03-28
Hi!

I'm currently trying to install the PHP-GTK.
I've download the newest source from here: [http://gtk.php.net/download.php](http://gtk.php.net/download.php)
Then i ran *./buildconf* with no errors, but when i do *./configure* I get this:

```
pontus@Pontus-PC:~/php-gtk$ ./configure
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... gawk
checking for PHP-GTK support... yes, shared
checking for PHP executable... found version 5.2.10-2ubuntu6.4
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysql.so' - /usr/lib/php5/20060613+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysqli.so' - /usr/lib/php5/20060613+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_mysql.so' - /usr/lib/php5/20060613+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
checking for gawk... (cached) gawk
checking whether to include debugging symbols... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0... yes (version 2.22.3)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.18.3)
checking for atk >= 1.9.0... yes
checking ATK_CFLAGS... -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking ATK_LIBS... -latk-1.0 -lgobject-2.0 -lglib-2.0  
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking for cairo >= 1.4.0... yes
checking CAIRO_CFLAGS... -D_REENTRANT -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12  
checking CAIRO_LIBS... -lcairo  
checking for cairo php extension... no
configure: error: cairo php extension not found.

```

After that I can't continue with make & make install, I get some kind of:
*make: *** No targets specified and no makefile found.  Stop.*


I hope this is easly fixed :D

---

### Post by Grozzy on 2010-03-28
Anyone?
I can't get it to work...

---

### Post by lbharti on 2010-12-26
Please follow [http://ubuntuforums.org/showthread.php?t=1471531](http://ubuntuforums.org/showthread.php?t=1471531)

---

