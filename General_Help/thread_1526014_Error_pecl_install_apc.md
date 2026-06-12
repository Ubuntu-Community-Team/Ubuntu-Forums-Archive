---
title: "Error: pecl install apc"
date: 2010-07-07
forum: General Help
---

### Post by solomojo on 2010-07-07
After a couple of hours of trying to figure-out how to install apc so  that I can setup multisite drupal on my ubuntu server I thought....  "The forum gurus will know"  So, here is my issue:

I have installed the following:

apt-get install apache2-mpm-worker
apt-get install apache2-threaded-dev
apt-get install perl
apt-get install php5
apt-get install php5-dev
apt-get install php-pear
apt-get install mysql-server

#SET SYMBOLIC LINK FOR apxs
ln -s /usr/bin/apxs2 /usr/bin/apxs

# THEN I RUN THE FOLLOWING COMMAND:

pecl install apc

# I ANSWER THE FOLLOWING QUESTION: 
Use apxs to set compile flags (if using APC with Apache)? [yes] : y

# I GET THE FOLLOWING:
----------------------------------------------------------------------------------------------
building in /var/tmp/pear-build-root/APC-3.0.19
running: /tmp/pear/temp/APC/configure --with-apxs=y
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
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
checking for PHP includes... -I/usr/include/php5  -I/usr/include/php5/main -I/usr/include/php5/TSRM  -I/usr/include/php5/Zend -I/usr/include/php5/ext  -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20090626
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to  regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking whether apc needs to get compiler flags from apxs...

Sorry, I was not able to successfully run APXS.  Possible reasons:

1.  Perl is not installed;
2.  Apache was not compiled with DSO support (--enable-module=so);
3.  'apxs' is not in your path.  Try to use --with-apxs=/path/to/apxs
The output of /var/tmp/pear-build-root/APC-3.0.19/y follows
/tmp/pear/temp/APC/configure: line 4113:  /var/tmp/pear-build-root/APC-3.0.19/y: No such file or directory
configure: error: Aborting
ERROR: `/tmp/pear/temp/APC/configure --with-apxs=y' failed

---------------------------------------------------------------------------------------------
1. I have confirmed that perl is installed.  

2. I'm not sure if DSO support is enabled (I don't know where the to  find the config.status file).

3. I have created a symbolic link for apxs (ln -s /usr/bin/apxs2  /usr/bin/apxs)


If you can help that would be great thanks.

---

### Post by helmi03 on 2010-08-02
sudo apt-get install php5-dev php-pear apache2-threaded-dev

pecl install apc

see: [http://getpesos.com/installing-apc-on-ubuntu-804-hardy-heron-1744.html](http://getpesos.com/installing-apc-on-ubuntu-804-hardy-heron-1744.html)

---

