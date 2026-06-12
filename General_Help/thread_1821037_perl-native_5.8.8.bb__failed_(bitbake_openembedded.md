---
title: "perl-native_5.8.8.bb  failed (bitbake openembedded)"
date: 2011-08-08
forum: General Help
---

### Post by benzan on 2011-08-08
Hi, all.

I try to get OpenEmbedded to work on the Mini2440. Bitbake starts from a script but ends after line 2008 with this error:

ERROR: '/oeroot/openembedded/recipes/perl/perl-native_5.8.8.bb' failed

Google points me to this reason for the error:

This error is due to Ubuntu 11.10 as they have moved the lib that clash with the compilation .... for now only remedy is to return with 10.10

Is there no other solution possible ?

I am running Ubuntu 11.04

Thanks,
Ben

---

### Post by alex-t on 2011-09-13
I'm not certain my error had the same cause as yours; googling shows that there is quite a lot of problems with openembedded/perl-native on different distros, but package maintainers blame particular distros and do nothing. I don't know who is right, but I found a workaround for my case, and hope that it will help others.

I'm building on  Ubuntu 11.04 Server. I had the following errors:
```
NOTE: Running task 109 of 173 (ID: 7, /home/b/ws/trunk/openembedded/recipes/perl/perl-native_5.8.8.bb, do_compile)
ERROR: function do_compile failed
ERROR: log data follows (/home/b/ws/trunk/tmp/work/i686-linux/perl-native-5.8.8-r14/temp/log.do_compile.4108)
| NOTE: make -e MAKEFLAGS=
| gcc -L/home/b/ws/trunk/tmp/staging/i686-linux/usr/lib -Wl,-rpath-link,/home/b/ws/trunk/tmp/staging/i686-linux/usr/lib -Wl,-rpath,/home/b/ws/trunk/tmp/staging/i686-linux/usr/lib -Wl,-O1 -L/usr/local/lib -o miniperl \
|           miniperlmain.o opmini.o libperl.a
| opmini.o: In function `Perl_scalar':
| opmini.c:(.text+0x4b96): undefined reference to `pthread_getspecific'

[COLOR=Green][ --- 8< --- a lot of complaints about pthreads stuff --- >8 --- ][/COLOR]

| libperl.a(pp.o): In function `Perl_pp_pow':
| pp.c:(.text+0x2d21): undefined reference to `pow'
| libperl.a(pp.o): In function `Perl_pp_modulo':
| pp.c:(.text+0x3822): undefined reference to `floor'
| pp.c:(.text+0x3849): undefined reference to `floor'
| pp.c:(.text+0x3be2): undefined reference to `fmod'
| libperl.a(pp.o): In function `Perl_pp_atan2':
| pp.c:(.text+0x89ba): undefined reference to `atan2'

[COLOR=Green][ --- 8< --- a lot of complaints about math stuff --- >8 --- ][/COLOR]

| collect2: ld returned 1 exit status
| make: *** [miniperl] Error 1
| FATAL: oe_runmake failed
NOTE: Task failed: /home/b/ws/trunk/tmp/work/i686-linux/perl-native-5.8.8-r14/temp/log.do_compile.4131
ERROR: TaskFailed event exception, aborting
ERROR: Build of /home/b/ws/trunk/openembedded/recipes/perl/perl-native_5.8.8.bb do_compile failed
ERROR: Task 7 (/home/b/ws/trunk/openembedded/recipes/perl/perl-native_5.8.8.bb, do_compile) failed
NOTE: Tasks Summary: Attempted 108 tasks of which 108 didn't need to be rerun and 1 failed.
ERROR: '/home/b/ws/trunk/openembedded/recipes/perl/perl-native_5.8.8.bb' failed

```Failing to find a proper fix, I went for symptomatic treatment, and it worked from the first attempt:

```
Index: perl-native_5.8.8.bb
===================================================================
--- perl-native_5.8.8.bb    (revision 3918)
+++ perl-native_5.8.8.bb    (working copy)
@@ -24,8 +24,8 @@
 do_configure () {
     ./Configure \
         -Dcc="${CC}" \
-        -Dcflags="${CFLAGS}" \
-        -Dldflags="${LDFLAGS}" \
+        -Dcflags="${CFLAGS} [COLOR=Red]-lpthread -lm[/COLOR]" \
+        -Dldflags="${LDFLAGS} [COLOR=Red]-lpthread -lm[/COLOR]" \
         -Dcf_by="Open Embedded" \
         -Dprefix=${prefix} \
         -Dvendorprefix=${prefix} \

```**NOTE**: Be sure to run [FONT=Courier New][COLOR=Purple]bitbake -c clean perl-native[/COLOR][/FONT] after applying the patch. On its own, bitbake won't notice the changes.

I'm pretty sure there is no need to patch *both* CFLAGS and LDFLAGS, but I have no desire to spend time figuring out which is the right one in this case; this whole issue wasted enough of my time as it is. 

Hope this helps someone.

---

### Post by benzan on 2011-10-07
Thanks a lot for your reply. It solved a big part of my problem.

However, some other problem shows up:

NOTE: Running task 590 of 2159 (ID: 1041, /oeroot/openembedded/recipes/intltool/intltool-native_0.40.3.bb, do_configure)
ERROR: function do_configure failed
ERROR: see log in /oeroot/build/work/i686-linux/intltool-native-0.40.3-r2/temp/log.do_configure.19465
NOTE: Task failed: /oeroot/build/work/i686-linux/intltool-native-0.40.3-r2/temp/log.do_configure.19465
ERROR: TaskFailed event exception, aborting
ERROR: Build of /oeroot/openembedded/recipes/intltool/intltool-native_0.40.3.bb do_configure failed
ERROR: Task 1041 (/oeroot/openembedded/recipes/intltool/intltool-native_0.40.3.bb, do_configure) failed
NOTE: Tasks Summary: Attempted 2024 tasks of which 2024 didn't need to be rerun and 1 failed.
ERROR: '/oeroot/openembedded/recipes/intltool/intltool-native_0.40.3.bb' failed

The log file which it point to tells me:
checking for XML:parser... configure: error: XML:parser perl module is required for intltool
FATAL: oe_runconf failed

libxml-parser-perl is installed. Checked (as found on different Google results) with

bitbake libxml-parser-perl-native but with the same error.

Did remove libxml-parser-perl and re-installed it, but the same result.
Did find one page with a test for checking the libxml-parser-perl availability
with /usr/bin/perl -e "require XML:parser"
but this test was passing without errors so it IS there..

Did read about 100 pages on the WWW about this error but none comes to the right solution for me.

Any help anyone ?

Thanks in advance,
Ben

---

