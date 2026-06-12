---
title: "need some help with e17"
date: 2006-04-20
forum: General Help
---

### Post by syklitengutt on 2006-04-20
Im trying to install E17 with
easy_e17.sh from this page:
[http://omicron.homeip.net/projects/]("http://omicron.homeip.net/projects/")
but I get an error at one step...
Anyone who can see whats wrong?


> LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ecore.log:
-----------------------------------------------------------------------------
make[4]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_file'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_file'
Making all in ecore_dbus
make[4]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib'
make[3]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib'
Making all in bin
make[3]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/bin'
/bin/sh ../../libtool --mode=link gcc  -I/opt/e17/include -g -O2 -Wall  -L/opt/e17/lib -o ecore_test  ecore_test-ecore_test.o ../../src/lib/ecore/libecore.la ../../src/lib/ecore_x/libecore_x.la ../../src/lib/ecore_txt/libecore_txt.la ../../src/lib/ecore_job/libecore_job.la ../../src/lib/ecore_fb/libecore_fb.la ../../src/lib/ecore_evas/libecore_evas.la ../../src/lib/ecore_con/libecore_con.la ../../src/lib/ecore_ipc/libecore_ipc.la -lm
gcc -I/opt/e17/include -g -O2 -Wall -o .libs/ecore_test ecore_test-ecore_test.o  -L/opt/e17/lib ../../src/lib/ecore/.libs/libecore.so ../../src/lib/ecore_x/.libs/libecore_x.so ../../src/lib/ecore_txt/.libs/libecore_txt.so ../../src/lib/ecore_job/.libs/libecore_job.so ../../src/lib/ecore_fb/.libs/libecore_fb.so ../../src/lib/ecore_evas/.libs/libecore_evas.so ../../src/lib/ecore_con/.libs/libecore_con.so ../../src/lib/ecore_ipc/.libs/libecore_ipc.so -lm
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_get'
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_set'
collect2: ld returned 1 exit status
make[3]: *** [ecore_test] Error 1
make[3]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore'
make: *** [all] Error 2


---

### Post by syklitengutt on 2006-04-20
is it something im missing?

---

### Post by rustikus on 2006-04-21
Perhaps you try it again. It is possible that there were some changes in CVS the broke some things. I have installed is yesterday after your post without problems.

---

### Post by syklitengutt on 2006-04-22
ive tried again... same problem....
Anyone who can read out of the errer whats the problem?

---

### Post by firecat53 on 2006-04-22
1. Delete the e17_cvs and e17 directories and try again.
2. If you previously tried to install e17 from a different source, go make sure you've COMPLETELY removed ALL the files. This can take some searching! Most of the stuff starts with e, but so do some important Gnome files (don't ask how I know this...)
3. Wait a couple of days and try again. CVS breaks sometimes.

Good luck!

Scott

---

### Post by syklitengutt on 2006-04-22
how can I find e files?
I know they  hav ebeen installed to  /opt/e|7
But my guess is that its more files outside that directory...
How can I find theese?

---

### Post by firecat53 on 2006-04-23
Heh, heh.....don't worry about the ones installed in /opt/e17 -- HOWEVER, look through those, as you can use those filenames as a guide to identifying the other ones you may find in your regular filesystem.
Try 'find / -name e*'.  That will spit back everything that starts with e. Or, more specifically, you can replace the / with /lib, /usr/lib, /usr/share/lib, /bin, /usr/bin/,/usr/share/bin, /usr/local/lib, /usr/local/bin, etc etc to just look in one directory at a time. I wish I could tell you an easier way!! 

If you've never tried to install e17  or e16 by any other means, then that's not the issue and don't waste your time. Just delete your e17_cvs and /opt/e17 and try again.

Good luck!
Scott

---

