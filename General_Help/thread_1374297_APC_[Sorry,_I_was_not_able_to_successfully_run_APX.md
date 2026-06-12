---
title: "APC [Sorry, I was not able to successfully run APX]"
date: 2010-01-06
forum: General Help
---

### Post by whisher on 2010-01-06
Hi,
I'm trying to install APC by
sudo pecl install apc
but with I get
> 
sudo pecl install apc 
downloading APC-3.0.19.tgz ...
Starting to download APC-3.0.19.tgz (115,735 bytes)
....................done: 115,735 bytes
47 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
 1. Use apxs to set compile flags (if using APC with Apache)? : yes

1-1, 'all', 'abort', or Enter to continue: 
building in /var/tmp/pear-build-root/APC-3.0.19
running: /tmp/pear/cache/APC-3.0.19/configure --with-apxs
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
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
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking whether apc needs to get compiler flags from apxs...

Sorry, I was not able to successfully run APXS.  Possible reasons:

1.  Perl is not installed;
2.  Apache was not compiled with DSO support (--enable-module=so);
3.  'apxs' is not in your path.  Try to use --with-apxs=/path/to/apxs
The output of apxs follows
/tmp/pear/cache/APC-3.0.19/configure: line 3888: apxs: command not found
configure: error: Aborting
ERROR: `/tmp/pear/cache/APC-3.0.19/configure --with-apxs' failed


Ubuntu 8.04
Can you help me, please ?

Bye.

---

### Post by chrislynch8 on 2010-01-11
Hi,

I was just looking at installing this and I came accros a post that said, in Ubuntu the apx is called apx2 so try the following

sudo ln -s /usr/bin/apxs2 /usr/bin/apxs

That should do the job.

Rgds
Chris

---

