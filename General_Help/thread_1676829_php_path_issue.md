---
title: "php path issue"
date: 2011-01-27
forum: General Help
---

### Post by acantha on 2011-01-27
I'm running 9.04 server, and whenever i run anything with php, i get the following error. it doesn't prevent me from executing the php, but its annoying. 

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs//usr/lib/php5/20090626/cairo.so' - /usr/lib/php5/20060613+lfs//usr/lib/php5/20090626/cairo.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs//usr/lib/php5/20090626/php_gtk2.so' - /usr/lib/php5/20060613+lfs//usr/lib/php5/20090626/php_gtk2.so: cannot open shared object file: No such file or directory in Unknown on line 0

it looks like two different paths got munged together.

i've attempted to remove --purge libgtk2.0 but i believe i installed cairo from source, which is potentially the problem but it was a really long time ago, so i don't recall what i might have done.

---

