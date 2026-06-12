---
title: "Installing harbour"
date: 2012-07-31
forum: General Help
---

### Post by eslavko on 2012-07-31
Hello...
I want to install harbour compiler. It came as source. 
But I can't compile it as I got error.

/usr/bin/ld: cannot find -lX11

I seek and try to find that library but can't find it.

Any hint?

Slavko.


system: Ubuntu 12.04/64 bit

---

### Post by Toz on 2012-08-06
From the harbour documentation, you need the following dependencies:
```
Linux (.deb based distros: Debian, Ubuntu)
   ------------------------------------------

      You'll need these base packages to build/package/test/use Harbour:

         $ sudo apt-get install bash subversion gcc binutils fakeroot debhelper valgrind upx uncrustify

      You'll need these packages to compile certain contribs and optional Harbour features:

      for gtcrs terminal lib:    $ sudo apt-get install libncurses-dev
      for gtsln terminal lib:    $ sudo apt-get install libslang2-dev OR
                                 $ sudo apt-get install libslang1-dev
      for gtxwc terminal lib:    $ sudo apt-get install libx11-dev
      for console mouse support: $ sudo apt-get install libgpm-dev OR
                                 $ sudo apt-get install libgpmg1-dev
      for contrib/gtalleg lib:   $ sudo apt-get install liballegro4.2-dev
      for contrib/hbcairo lib:   $ sudo apt-get install libcairo2-dev
      for contrib/hbcups lib:    $ sudo apt-get install libcups2-dev
      for contrib/hbcurl lib:    $ sudo apt-get install libcurl4-openssl-dev OR
                                 $ sudo apt-get install libcurl4-gnutls-dev
      for contrib/hbexpat lib:   $ sudo apt-get install libexpat1-dev
      for contrib/hbfbird lib:   $ sudo apt-get install firebird2.1-dev OR
                                 $ sudo apt-get install libfirebird2.0-dev
      for contrib/hbfimage lib:  $ sudo apt-get install libfreeimage-dev
      for contrib/hbgd lib:      $ sudo apt-get install libgd2-xpm-dev OR
                                 $ sudo apt-get install libgd-xpm-dev
      for contrib/hbgs lib:      $ sudo apt-get install libgs-dev
      for contrib/hbmagic lib:   $ sudo apt-get install libmagic-dev
      for contrib/hbmysql lib:   $ sudo apt-get install libmysqlclient15-dev
      for contrib/hbodbc lib:    $ sudo apt-get install unixodbc-dev
      for contrib/hbpgsql lib:   $ sudo apt-get install libpq-dev
      for contrib/hbqt lib:      $ sudo apt-get install libqt4-dev

      Optional, to override locally hosted sources:

      for bzip2 support:         $ sudo apt-get install libbz2-dev
      for zlib support:          $ sudo apt-get install zlib1g-dev
      for pcre (regex) support:  $ sudo apt-get install libpcre3-dev
      for contrib/hbsqlit3 lib:  $ sudo apt-get install libsqlite3-dev
```

I'm guessing that it's libx11-dev that it's complaining about. 

Note: pre-built ubuntu binaries are available, to save you the headache of building it yourself. See: [http://sourceforge.net/projects/harbour-project/files/binaries-linux-ubuntu/]("http://sourceforge.net/projects/harbour-project/files/binaries-linux-ubuntu/").

---

### Post by eslavko on 2012-08-07
Installing prebuild helps...

Thanks

---

