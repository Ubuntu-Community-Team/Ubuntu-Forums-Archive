---
title: "opt/e17/bin/enlightenment"
date: 2006-02-08
forum: General Help
---

### Post by Ubuntuud on 2006-02-08
Hi, I installed e17 by following a howto on this forum, but when I start it I get a message and Gnome starts up.
The mesaage says something like, can't find nor open /opt/e17/bin/enlightenment
Any ideas? Can I download this file/directory? Thanks.

---

### Post by trorion on 2006-02-16
Your e17 install failed (see code below).  I have the same error and numerous others have had an identical error.  It may be due to a failed portion of the CVS download (earlier in the code it most likely indicated that it couldn't find "/root/.cvsblahblah" but I don't know if that's the problem.

I'm currently reading the 20 pages of "how to" to see if anyone figured it out.

```
ranlib .libs/libecore_dbus.a
creating libecore_dbus.la
(cd .libs && rm -f libecore_dbus.la && ln -s ../libecore_dbus.la libecore_dbus.la)
make[4]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Entering directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
make[3]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
Making all in bin
make[3]: Entering directory `/home/owner/e17_cvs/e17/libs/ecore/src/bin'
if gcc-3.4 -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include  -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -MT ecore_test-ecore_test.o -MD -MP -MF ".deps/ecore_test-ecore_test.Tpo" -c -o ecore_test-ecore_test.o `test -f 'ecore_test.c' || echo './'`ecore_test.c; \
then mv -f ".deps/ecore_test-ecore_test.Tpo" ".deps/ecore_test-ecore_test.Po"; else rm -f ".deps/ecore_test-ecore_test.Tpo"; exit 1; fi
/bin/sh ../../libtool --tag=CC --mode=link gcc-3.4  -I/opt/e17/include -g -O2 -Wall  -L/opt/e17/lib -o ecore_test  ecore_test-ecore_test.o ../../src/lib/ecore/libecore.la ../../src/lib/ecore_x/libecore_x.la ../../src/lib/ecore_txt/libecore_txt.la ../../src/lib/ecore_job/libecore_job.la ../../src/lib/ecore_fb/libecore_fb.la ../../src/lib/ecore_evas/libecore_evas.la ../../src/lib/ecore_con/libecore_con.la ../../src/lib/ecore_ipc/libecore_ipc.la -lm
mkdir .libs
gcc-3.4 -I/opt/e17/include -g -O2 -Wall -o .libs/ecore_test ecore_test-ecore_test.o  -L/opt/e17/lib ../../src/lib/ecore/.libs/libecore.so ../../src/lib/ecore_x/.libs/libecore_x.so ../../src/lib/ecore_txt/.libs/libecore_txt.so ../../src/lib/ecore_job/.libs/libecore_job.so ../../src/lib/ecore_fb/.libs/libecore_fb.so ../../src/lib/ecore_evas/.libs/libecore_evas.so ../../src/lib/ecore_con/.libs/libecore_con.so ../../src/lib/ecore_ipc/.libs/libecore_ipc.so -lm
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_get'
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_set'
collect2: ld returned 1 exit status
make[3]: *** [ecore_test] Error 1
make[3]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore'
make: *** [all] Error 2
```

---

### Post by Ubuntuud on 2006-02-16
I figured it out myself. What you should do is get another version of e17, _not_ through cvs (I forgot where I got it, I believe it is on one of the 3 or 4 howtos) Install that version and after that install the one they use on the howto you used.
I know that they do not recommend it, but it worked for me... Hope this is of any use to you.

---

### Post by trorion on 2006-02-16
Thanks!

I've only tried to install the program for 2 or 3 hours (1 night) so I guess I'm doing pretty well.  Last time I tried linux was in '99 so I'm used to 4-5 hour installs of basic programs.

When you say that you got a copy from a different location I assume you mean that you just downloaded it and expanded it into a directory then ran the script pretty much exactly as the original "Howto" shows right?  Now I'm going to show my newbness...where did you un-zip it to?

---

### Post by Ubuntuud on 2006-02-16
First, could you post me a link to the howto you're using, because there are several.
And second, well, there isn't really a second, that one will come once I know what howto you're using.

---

### Post by trorion on 2006-02-16
[QUOTE=Ubuntuud]First, could you post me a link to the howto you're using, because there are several.
And second, well, there isn't really a second, that one will come once I know what howto you're using.[/QUOTE]
Using: [http://ubuntuforums.org/showthread.php?t=97199&highlight=howto+e17]("http://ubuntuforums.org/showthread.php?t=97199&highlight=howto+e17") and I really appreciate your help here.  I love the idea that linux might become competitive visually and functionally with windows/mac.

---

### Post by Ubuntuud on 2006-02-16
Great! It's the same one I used...
Now the installation file... I forgot where I got it from, but I managed to find it hanging around on my directory. There are two things you can do.
The first is give me your email, don't wory, the file is less then 30 KB (internet install.) You can do this with a personal message if you don't want it to get public.
The second option is to go and search it yourself, it is called "get_e.sh". I allready tried to find it in the wiki because I thought that I downloaded it from there, but without any succes.
Well, tell me what your decision is, I will help you search if you want a website to download it from but I'm currently not very motivated. Because if you would like to get it e-mailed it would be a waste of time...

And btw, it's a pleasure helping you. I always find it fun to help people who are older, it makes me feel smart. (If you're wondering how I know you're older, in '99 I was seven...)

---

### Post by Ubuntuud on 2006-02-16
UPDATE: I might have found a site with the file [http://www3.get-e.org/E17_User_Guide/English/_pages/2.1.html](http://www3.get-e.org/E17_User_Guide/English/_pages/2.1.html). It isn't the one I used but I think it'll do it, it might even work on it's own...
Hope this is useful

---

