---
title: "Lucid: attempting install of ruby gem 'mysql'"
date: 2010-09-02
forum: General Help
---

### Post by holocene on 2010-09-02
==========
NOTE: subsequent to posting, I attempted to use the gem 'mysql' and it worked. This is odd considering all the errors that were emitted below. Anyway, I can proceed with my study.
==========


Greetings,

Environment:
Running 10.04
MySQL version: mysql  Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (i486) using readline 6.1
Ruby: ruby 1.8.7 (2010-01-10 patchlevel 249) [i486-linux]

I am trying to install the ruby gem 'mysql'.
From my reading, I should be able to do a:
$gem install mysql 

By the way, using sudo or not has same result. 

This is disappointing because I have done a lot of work to learn MySQL only to discover that I can not use it with Ruby (at least with this gem).

I routinely use $mysql so I would "guess" that the mysqlclient is working.

Any help greatly appreciated.
steve. 



Here are the errors:
holocene@crypt:~/mysql-ruby-2.8.2$ sudo gem install mysql
[sudo] password for holocene: 
Building native extensions.  This could take a while...
ERROR:  Error installing mysql:
    ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lm... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lz... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lsocket... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lnsl... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lmygcc... no
checking for mysql_query() in -lmysqlclient... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

---

### Post by mattwilmott on 2011-03-16
I believe you need to install the header files to resolve this issue

try

sudo apt-get install ruby1.8-dev

and try again

---

