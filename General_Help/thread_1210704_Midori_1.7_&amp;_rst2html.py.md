---
title: "Midori 1.7 &amp; rst2html.py"
date: 2009-07-11
forum: General Help
---

### Post by Scrifter on 2009-07-11
Hi

Im try to install Midori 1.7 dont know how to get rst2html.py

./configure
Checking for Python			:  033[92m/usr/bin/python033[0m
Checking for WAF			:  033[92m/home/dude/Desktop/midori-0.1.7/waf033[0m
calling waf configure with parameters
Checking for program gcc                 : ok /usr/bin/gcc 
Checking for program cpp                 : ok /usr/bin/cpp 
Checking for program ar                  : ok /usr/bin/ar 
Checking for program ranlib              : ok /usr/bin/ranlib 
Checking for gcc                         : ok  
Checking for program glib-genmarshal     : ok /usr/bin/glib-genmarshal 
Checking for program glib-mkenums        : ok /usr/bin/glib-mkenums 
Checking for program rst2html.py         : not found 
Checking for program rst2html            : ok /usr/bin/rst2html 
Checking for program msgfmt              : ok /usr/bin/msgfmt 
Checking for program intltool-merge      : ok /usr/bin/intltool-merge 
Checking for header locale.h             : ok 
Checking for unique-1.0 >= 0.9           : ok 
Checking for libidn >= 1.0               : ok 
Checking for sqlite3 >= 3.0              : ok 
Checking for library m                   : ok 
Checking for gmodule-2.0 >= 2.8.0        : ok 
Checking for gthread-2.0 >= 2.8.0        : ok 
Checking for gio-2.0 >= 2.16.0           : ok 
Checking for gtk+-2.0 >= 2.10.0          : ok 
Checking for webkit-1.0 >= 1.1.1         :  
/home/dude/Desktop/midori-0.1.7/wscript:114: error: the configuration failed (see '/home/dude/Desktop/midori-0.1.7/_build_/config.log')

any help woud be appreciated

---

### Post by blueled on 2010-01-14
I have the same problem with the latest version 0.2.2

```
angelos@angelos-desktop:~/bin/midori-0.2.2$ ./waf configure
Checking for program gcc                 : ok /usr/bin/gcc 
Checking for program cpp                 : ok /usr/bin/cpp 
Checking for program ar                  : ok /usr/bin/ar 
Checking for program ranlib              : ok /usr/bin/ranlib 
Checking for gcc                         : ok  
Checking for program glib-genmarshal     : ok /usr/bin/glib-genmarshal 
Checking for program glib-mkenums        : ok /usr/bin/glib-mkenums 
Checking for program rst2html.py         : not found 
Checking for program rst2html            : ok /usr/bin/rst2html 
Checking for program msgfmt              : ok /usr/bin/msgfmt 
Checking for program intltool-merge      : ok /usr/bin/intltool-merge 
Checking for header locale.h             : ok 
Checking for program rsvg-convert        : ok /usr/bin/rsvg-convert 
Checking for unique-1.0 >= 0.9           : ok 
Checking for sqlite3 >= 3.0              : ok 
Checking for libnotify >=                : ok 
Checking for library m                   : ok 
Checking for gmodule-2.0 >= 2.8.0        : ok 
Checking for gthread-2.0 >= 2.8.0        : ok 
Checking for gio-2.0 >= 2.16.0           : ok 
Checking for x11 >=                      : ok 
Checking for gtk+-2.0 >= 2.10.0          : ok 
Checking for webkit-1.0 >= 1.1.1         :  
/home/angelos/bin/midori-0.2.2/wscript:172: error: the configuration failed (see '/home/angelos/bin/midori-0.2.2/_build_/config.log')

```any hint appreciated ...

**update**: I remove "python-docutils" that I installed from the repositories and downloaded the latest version from [http://docutils.sourceforge.net](http://docutils.sourceforge.net) (and installed it of course)

the dependencies are fixed , but midori still cannot be installed :(

/home/angelos/bin/midori-0.2.2/wscript:172: error: the configuration failed (see '/home/angelos/bin/midori-0.2.2/_build_/config.log')

**update**: solution in the comments [http://brainwreckedtech.wordpress.com/2009/05/21/howto-compile-midori-from-source-in-ubuntu/](http://brainwreckedtech.wordpress.com/2009/05/21/howto-compile-midori-from-source-in-ubuntu/)

---

