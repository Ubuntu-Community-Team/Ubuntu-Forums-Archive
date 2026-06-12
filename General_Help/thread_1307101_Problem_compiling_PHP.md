---
title: "Problem compiling PHP"
date: 2009-10-30
forum: General Help
---

### Post by Naminator_X_ on 2009-10-30
I downloaded the latest sources from php.net (5.3.0) user ./configure with few flags ...no errors...i typed make && make install and i got some strange errors. In google i read it's because th gcc compiler...but since i dont want to mess up my compiler i will post the infos here if u get any better ideas.

The ./configure line:
./configure --prefix=/usr/local/php/ --enable-mbstring --with-mcrypt --with-mysql=/usr/lib/mysql/ --with-mysqli 

The error on "make" (without quotes)
pt -lxml2 -lxml2 -lxml2 -lcrypt  -o sapi/cgi/php-cgi
/usr/bin/ld: cannot find -lltdl
collect2: ld returned 1 exit status
make: *** [sapi/cgi/php-cgi] Error 1

Despite the fact i have 0 errors in ./configure... :(

---

### Post by Naminator_X_ on 2009-10-31
Ok i've read somewhere that i have to put this somewhere

CFLAGS="-O0"

in the source to somehow force the compiler to user the old style of compiling...but in which file ? Or i should add it at the end of make ? O.O

---

### Post by dragontux on 2009-11-22
I have found that installing libmhash-dev package fix it. 

Good luck. ;)

---

