---
title: "Update path with a new shell script"
date: 2011-01-12
forum: General Help
---

### Post by micha8l on 2011-01-12
I've had pear installed on my system for a while now, but recently I've started using The Zend Server Community Edition (with Zend Framework) which comes with a preconfigured pear shell script configured for the framework. I would like instead to use Zend's Pear shell script, but when I type pear from BASH it invokes my old pear shell script. Is there a way I can use Zend's shell script instead?

---

### Post by hawkmage on 2011-01-12
There are a number of places that the path could be set.  Look in /etc/profile /etc/bash.bashrc also there can be scripts in /etc/profile.d/ also in your home directory .profile or .bash_profile or .bashrc.

All you have to do is make sure that the directory for Zend is on the path before old one.

---

### Post by micha8l on 2011-01-12
Thanks for the reply hawkmage. I checked /etc/profile, ~.bashrc, /root/.bashrc, /etc/bash.bashrc and couldn't find one mention of the Pear path. Is there a way I can list all paths for a user, or is there any master path file that has precedence over the rest?

---

### Post by micha8l on 2011-01-13
Got it!

It seems some programs set there shell configuration options within independent directories. I looked in /etc/pear and found pear.conf and replaced this with /usr/local/zend/etc/pear.conf.  I know this works because now when I run:

```

pear config-show

```It returns:

> 
...
PEAR executables directory     bin_dir          /usr/local/zend/bin
PEAR documentation directory   doc_dir          /usr/local/zend/share/pear/doc
PHP extension directory        ext_dir          /usr/local/zend/lib/php/20090626
PEAR directory                 php_dir          /usr/local/zend/share/pear
PEAR Installer cache directory cache_dir        /tmp/pear/cache
PEAR configuration file        cfg_dir          /usr/local/zend/share/pear/cfg
directory
PEAR data directory            data_dir         /usr/local/zend/share/pear/data
PEAR Installer download        download_dir     /tmp/pear/download
directory
PHP CLI/CGI binary             php_bin          /usr/local/zend/bin/php
php.ini location               php_ini          <not set>
--program-prefix passed to     php_prefix       <not set>
PHP's ./configure
--program-suffix passed to     php_suffix       <not set>
PHP's ./configure
PEAR Installer temp directory  temp_dir         /tmp/pear/temp
PEAR test directory            test_dir         /usr/local/zend/share/pear/test
PEAR www files directory       www_dir          /usr/local/zend/share/pear/htdocs
...
Phew, that was not easy. Thaks again for putting me on the right track.

---

