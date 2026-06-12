---
title: "etherape won't run in Lucid"
date: 2010-05-12
forum: General Help
---

### Post by Aquila99 on 2010-05-12
I have just updated to Lucid, and all seemed to go well except for one issue.

etherape won't start when I run it as root.
When I start it with a normal user, it starts OK, but I cannot access eth0 which I want to monitor.

From the command line:

peter@trinity:~$ sudo etherape 

(etherape:21611): GLib-CRITICAL **: g_ascii_strcasecmp: assertion `s2 != NULL' failed
Segmentation fault
peter@trinity:~$ sudo etherape  -v

(etherape:21613): GLib-CRITICAL **: g_ascii_strcasecmp: assertion `s2 != NULL' failed
*** glibc detected *** etherape: munmap_chunk(): invalid pointer: 0x08f3aa0a ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x1ec4591]
/lib/tls/i686/cmov/libc.so.6(+0x6c80e)[0x1ec580e]
/lib/libglib-2.0.so.0(g_free+0x36)[0x72dfc6]
/lib/libglib-2.0.so.0(g_strfreev+0x20)[0x746e40]
etherape(protohash_compact+0x154)[0x8065a74]
etherape(load_config+0x323)[0x80566d3]
etherape(main+0x3fb)[0x8056c5b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x1e6fbd6]
etherape[0x8051501]
======= Memory map: ========
00110000-00126000 r-xp 00000000 08:01 2238664    /usr/lib/libglade-2.0.so.0.0.7
00126000-00127000 r--p 00015000 08:01 2238664    /usr/lib/libglade-2.0.so.0.0.7
00127000-00128000 rw-p 00016000 08:01 2238664    /usr/lib/libglade-2.0.so.0.0.7
00128000-0024c000 r-xp 00000000 08:01 2237710    /usr/lib/libxml2.so.2.7.6
0024c000-00250000 r--p 00123000 08:01 2237710    /usr/lib/libxml2.so.2.7.6
00250000-00251000 rw-p 00127000 08:01 2237710    /usr/lib/libxml2.so.2.7.6
00251000-00252000 rw-p 00000000 00:00 0 
00252000-00267000 r-xp 00000000 08:01 2237185    /usr/lib/libICE.so.6.3.0
00267000-00268000 r--p 00014000 08:01 2237185    /usr/lib/libICE.so.6.3.0
00268000-00269000 rw-p 00015000 08:01 2237185    /usr/lib/libICE.so.6.3.0
00269000-0026b000 rw-p 00000000 00:00 0 
0026b000-002c5000 r-xp 00000000 08:01 2240254    /usr/lib/libbonoboui-2.so.0.0.0
002c5000-002c6000 r--p 00059000 08:01 2240254    /usr/lib/libbonoboui-2.so.0.0.0
002c6000-002c8000 rw-p 0005a000 08:01 2240254    /usr/lib/libbonoboui-2.so.0.0.0
002c8000-002d2000 r-xp 00000000 08:01 2238776    /usr/lib/libpangocairo-1.0.so.0.2800.0
002d2000-002d3000 r--p 00009000 08:01 2238776    /usr/lib/libpangocairo-1.0.so.0.2800.0
002d3000-002d4000 rw-p 0000a000 08:01 2238776    /usr/lib/libpangocairo-1.0.so.0.2800.0
002d4000-002d8000 r-xp 00000000 08:01 2238512    /usr/lib/libgthread-2.0.so.0.2400.0
002d8000-002d9000 r--p 00003000 08:01 2238512    /usr/lib/libgthread-2.0.so.0.2400.0
002d9000-002da000 rw-p 00004000 08:01 2238512    /usr/lib/libgthread-2.0.so.0.2400.0
002dc000-002f0000 r-xp 00000000 08:01 2239006    /usr/lib/libgnome-2.so.0.3000.0
002f0000-002f1000 r--p 00013000 08:01 2239006    /usr/lib/libgnome-2.so.0.3000.0
002f1000-002f2000 rw-p 00014000 08:01 2239006    /usr/lib/libgnome-2.so.0.3000.0
002f2000-00343000 r-xp 00000000 08:01 2237112    /usr/lib/libbonobo-2.so.0.0.0
00343000-00344000 ---p 00051000 08:01 2237112    /usr/lib/libbonobo-2.so.0.0.0
00344000-00347000 r--p 00051000 08:01 2237112    /usr/lib/libbonobo-2.so.0.0.0
00347000-0034e000 rw-p 00054000 08:01 2237112    /usr/lib/libbonobo-2.so.0.0.0
0034e000-00361000 r-xp 00000000 08:01 2237786    /usr/lib/libbonobo-activation.so.4.0.0
00361000-00362000 r--p 00012000 08:01 2237786    /usr/lib/libbonobo-activation.so.4.0.0
00362000-00363000 rw-p 00013000 08:01 2237786    /usr/lib/libbonobo-activation.so.4.0.0
00363000-00364000 rw-p 00000000 00:00 0 
00364000-003f7000 r-xp 00000000 08:01 2238332    /usr/lib/libgdk-x11-2.0.so.0.2000.0
003f7000-003f9000 r--p 00093000 08:01 2238332    /usr/lib/libgdk-x11-2.0.so.0.2000.0
003f9000-003fa000 rw-p 00095000 08:01 2238332    /usr/lib/libgdk-x11-2.0.so.0.2000.0
003fa000-00413000 r-xp 00000000 08:01 2239550    /usr/lib/libatk-1.0.so.0.3009.1
00413000-00414000 ---p 00019000 08:01 2239550    /usr/lib/libatk-1.0.so.0.3009.1
00414000-00415000 r--p 00019000 08:01 2239550    /usr/lib/libatk-1.0.so.0.3009.1
00415000-00416000 rw-p 0001a000 08:01 2239550    /usr/lib/libatk-1.0.so.0.3009.1
00416000-0043b000 r-xp 00000000 08:01 2240010    /usr/lib/libpangoft2-1.0.so.0.2800.0
0043b000-0043c000 r--p 00024000 08:01 2240010    /usr/lib/libpangoft2-1.0.so.0.2800.0
0043c000-0043d000 rw-p 00025000 08:01 2240010    /usr/lib/libpangoft2-1.0.so.0.2800.0
0043d000-00440000 r-xp 00000000 08:01 2238359    /usr/lib/libgmodule-2.0.so.0.2400.0
00440000-00441000 r--p 00002000 08:01 2238359    /usr/lib/libgmodule-2.0.so.0.2400.0
00441000-00442000 rw-p 00003000 08:01 2238359    /usr/lib/libgmodule-2.0.so.0.2400.0
00442000-00444000 r-xp 00000000 08:01 1034552    /lib/tls/i686/cmov/libdl-2.11.1.so
00444000-00445000 r--p 00001000 08:01 1034552    /lib/tls/i686/cmov/libdl-2.11.1.so
00445000-00446000 rw-p 00002000 08:01 1034552    /lib/tls/i686/cmov/libdl-2.11.1.so
00446000-00449000 r-xp 00000000 08:01 1015893    /lib/libuuid.so.1.3.0
00449000-0044a000 r--p 00002000 08:01 1015893    /lib/libuuid.so.1.3.0
0044a000-0044b000 rw-p 00003000 08:01 1015893    /lib/libuuid.so.1.3.0
0044b000-0044d000 r-xp 00000000 08:01 2237526    /usr/lib/libavahi-glib.so.1.0.1
0044d000-0044e000 r--p 00001000 08:01 2237526    /usr/lib/libavahi-glib.so.1.0.1
0044e000-0044f000 rw-p 00002000 08:01 2237526    /usr/lib/libavahi-glib.so.1.0.1
0044f000-00451000 r-xp 00000000 08:01 1034568    /lib/tls/i686/cmov/libutil-2.11.1.so
00451000-00452000 r--p 00001000 08:01 1034568    /lib/tls/i686/cmov/libutil-2.11.1.so
00452000-00453000 rw-p 00002000 08:01 1034568    /lib/tls/i686/cmov/libutil-2.11.1.so
00453000-00457000 r-xp 00000000 08:01 2238345    /usr/lib/libORBitCosNaming-2.so.0.1.0
00457000-00458000 r--p 00003000 08:01 2238345    /usr/lib/libORBitCosNaming-2.so.0.1.0
00458000-00459000 rw-p 00004000 08:01 2238345    /usr/lib/libORBitCosNaming-2.so.0.1.0
0045a000-004f4000 r-xp 00000000 08:01 2238653    /usr/lib/libgio-2.0.so.0.2400.0
004f4000-004f5000 ---p 0009a000 08:01 2238653    /usr/lib/libgio-2.0.so.0.2400.0
004f5000-004f6000 r--p 0009a000 08:01 2238653    /usr/lib/libgio-2.0.so.0.2400.0
004f6000-004f7000 rw-p 0009b000 08:01 2238653    /usr/lib/libgio-2.0.so.0.2400.0
004f7000-004f8000 rw-p 00000000 00:00 0 
004f8000-0050d000 r-xp 00000000 08:01 1034563    /lib/tls/i686/cmov/libpthread-2.11.1.so
0050d000-0050e000 r--p 00014000 08:01 1034563    /lib/tls/i686/cmov/libpthread-2.11.1.so
0050e000-0050f000 rw-p 00015000 08:01 1034563    /lib/tls/i686/cmov/libpthread-2.11.1.so
0050f000-00511000 rw-p 00000000 00:00 0 
00511000-00517000 r-xp 00000000 08:01 2237984    /usr/lib/libgailutil.so.18.0.1
00517000-00518000 r--p 00005000 08:01 2237984    /usr/lib/libgailutil.so.18.0.1
00518000-00519000 rw-p 00006000 08:01 2237984    /usr/lib/libgailutil.so.18.0.1
0051c000-00540000 r-xp 00000000 08:01 1034553    /lib/tls/i686/cmov/libm-2.11.1.so
00540000-00541000 r--p 00023000 08:01 1034553    /lib/tls/i686/cmov/libm-2.11.1.so
00541000-00542000 rw-p 00024000 08:01 1034553    /lib/tls/i686/cmov/libm-2.11.1.so
00542000-00570000 r-xp 00000000 08:01 2237178    /usr/lib/libfontconfig.so.1.4.4
00570000-00571000 r--p 0002d000 08:01 2237178    /usr/lib/libfontconfig.so.1.4.4
00571000-00572000 rw-p 0002e000 08:01 2237178    /usr/lib/libfontconfig.so.1.4.4Aborted
peter@trinity:~$ 



In the previous version (Karmic), all was good.

The version of etherape is 0.9.8-1

Any ideas?  Not even sure where to start on this one!

Cheers, Peter

---

### Post by mkvnmtr on 2010-05-12
If you did an upgrade your problem might be that the program is set up for 9.10 and missing something . You could uninstall and reinstall from the 10.04 repositories and that should get every thing it depends on. I would also look in the home directory for a hidden configuration file and delete that before the reinstall.

---

### Post by iponeverything on 2010-05-12
Rebuilding the deb might solve your problem.  

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

---

### Post by Aquila99 on 2010-05-12
hi mkvnmtr - thanks for the fast response :-)

Firstly, searched in my home directory, and there were no files or directoies called ".etherape" or anything line that (is this what you meant?

then did the following:
  sudo apt-get remove etherape
  sudo apt-get install etherape
  sudo etherape
Get exactly the same result...
Any other ideas?
Cheers

---

### Post by Aquila99 on 2010-05-15
Have tried recompile from the sources, exactly the same issue.
Although I suspected that this would be the case as I only get this error when running with sudo.  Running as an ordinary user does at least bring up the window.

Any other ideas ... please ...

---

### Post by davidsrsb on 2010-05-18
I have a menu command:
su-to-root -X -c /usr/bin/etherape

which works fine

---

### Post by Aquila99 on 2010-05-18
Same thing.
From the command line:


peter@trinity:~$ su-to-root -X -c /usr/bin/etherape -i eth0
(etherape:22139): GLib-CRITICAL **: g_ascii_strcasecmp: assertion `s2 != NULL' failed
peter@trinity:~$

I am thinking that something in my configuration god screwed, but not sure how to figure it out.

---

### Post by davidsrsb on 2010-05-18
Is this a clean 10.04 install, an upgrade from 9.10 or via betas?

---

### Post by teh_drizzle on 2010-05-18
Maybe gksudo etherape might work?

---

### Post by teh_drizzle on 2010-05-18
You could also try exporting and importing your gConf settings. (I've only used this for modifying live CDs so I'm not sure what effect it will have for your root user.)

The reason I'm suggesting this is because this thread ([http://issues.foresightlinux.com/browse/FL-595?page=com.atlassian.jira.plugin.system.issuetabpanels:all-tabpanel](http://issues.foresightlinux.com/browse/FL-595?page=com.atlassian.jira.plugin.system.issuetabpanels:all-tabpanel)) seems to elude to trouble with the gnome configuration for the root user.

As your normal user:

gconftool-2 --dump / > settings.xml

As root:

gconftool-2 --load settings.xml

Good luck

---

### Post by Aquila99 on 2010-05-22
Thanks for your thoughts.

Confirming this is an upgraded system from 9.04 to 10.04 (that is when the problem began - etherape worked great in 9.04

tried "gksudo etherape" as suggested - exactly the same errors

tried loading the gkconf setting as suggested, same error.

Any ideas on where to go here?
This is getting very frustrating - I am feeling that there must be an old library or something lying around - but no idea how to check.


Cheers
Peter

---

### Post by Aquila99 on 2010-05-22
Yay!  :P
Finally figured it out ... the post about gconf gave me an idea that it might be to do with a "stale" configuration file.

So, I used "sudo strace etherape" to see all the files that it was reading.

Just before the crash, it opened "/root/.gnome2/Etherape"

Removed this file and all is happy again.
Will have to remember this strategy for other issues (and hopefully it might help other people.

Cheers,
Peter

---

### Post by bturig on 2010-06-26
Awesome!

deleting "/root/.gnome2/Etherape" worked for me.

Thanks for your persistence.

---

