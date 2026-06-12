---
title: "Firefox 3.0.12 crashing randomly - segmentation fault"
date: 2009-08-03
forum: General Help
---

### Post by gluonman on 2009-08-03
I'm using Ubuntu 9.04 and Firefox 3.0.12. Lately Firefox has been crashing each session after running for a random length of time. So I ran firefox from terminal and got the following output after it crashed:

```
gluonman@StrangeQuark:~$ firefox
unhandled event 19
Loading stream: http://mail.google.com/mail/im/media-api.swf?ver=1.0.0
unhandled event 19
unhandled event 19
Loading stream: http://mail.google.com/mail/im/chatsound.swf
Loading stream: http://mail.google.com/mail/im/sound.swf
Segmentation fault
gluonman@StrangeQuark:~$
```

I then ran it in gdb and backtraced for the following output (excerpts):

```
gluonman@StrangeQuark:~$ cd /usr/lib/firefox-3.0.12
gluonman@StrangeQuark:/usr/lib/firefox-3.0.12$ ./run-mozilla.sh -g firefox -d gdb
MOZILLA_FIVE_HOME=.
  LD_LIBRARY_PATH=.:./plugins:.
DISPLAY=:0.0
DYLD_LIBRARY_PATH=.:.
     LIBRARY_PATH=.:./components:.
       SHLIB_PATH=.:.
          LIBPATH=.:.
       ADDON_PATH=.
      MOZ_PROGRAM=firefox
      MOZ_TOOLKIT=
        moz_debug=1
     moz_debugger=
/usr/bin/gdb firefox -x /tmp/mozargs.ggzcTq
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/lib/firefox-3.0.12/firefox '-d' 'gdb'
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb7db16d0 (LWP 5197)]
.
.
.
[New Thread 0xb5abbb90 (LWP 5202)]
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb51afb90 (LWP 5203)]
(no debugging symbols found)
[New Thread 0xb4948b90 (LWP 5204)]
[Thread 0xb4948b90 (LWP 5204) exited]
[New Thread 0xb4948b90 (LWP 5205)]
.
.
.
[New Thread 0xb3f7bb90 (LWP 5208)]
[Thread 0xb3f7bb90 (LWP 5208) exited]
[New Thread 0xb3f7bb90 (LWP 5209)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb3679b90 (LWP 5210)]
[New Thread 0xb2e78b90 (LWP 5211)]
[New Thread 0xb2677b90 (LWP 5212)]
[New Thread 0xb1e62b90 (LWP 5213)]
[Thread 0xb4948b90 (LWP 5205) exited]
.
.
.
Loading stream: http://us.mg4.mail.yahoo.com/dc/cg_cookies.swf
unhandled event 19
Loading stream: http://m1.2mdn.net/1420759/lmb_iau_MenuMkYrCarColorRedCNPBd15s40k_ObBacks_TP_0709_300x250.swf
Loading stream: http://img-cdn.mediaplex.com/0/12309/81339/808346_CON_100111_SYS_STUDNOTE_BA_HERE_INTEL_160x600.swf
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
unhandled event 19
Loading stream: http://mail.google.com/mail/im/media-api.swf?ver=1.0.0
unhandled event 19
unhandled event 19
Loading stream: http://mail.google.com/mail/im/sound.swf
Loading stream: http://mail.google.com/mail/im/chatsound.swf

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb2677b90 (LWP 5212)]
0xb7e2c8aa in memcpy () from /lib/tls/i686/cmov/libc.so.6
(gdb) Quit
(gdb) bt
#0  0xb7e2c8aa in memcpy () from /lib/tls/i686/cmov/libc.so.6
Cannot access memory at address 0xb2676338
(gdb) 
[1]+  Stopped                 ./run-mozilla.sh -g firefox -d gdb
gluonman@StrangeQuark:/usr/lib/firefox-3.0.12$ cd
gluonman@StrangeQuark:~$
```

The only difference in running firefox with gdb is that instead of crashing when it receives the signal, it freezes and needs to be force quit.

Anyone know what I should do to solve this problem?

---

### Post by llamabr on 2009-08-03
wow, I havn't seen a seg fault in years.

Have you installed any addons or plugins?  try a fresh install:

```
mv .mozilla/ .mozilla.text/
```

and restart firefox.  Sometimes when you've had the same config files for several generations, you get some inconsistencies.  If so, you can just reinstall all of your old plugins and bookmarks one at a time.

It's a big hammer, but useful as a last resort.

---

### Post by csmgj on 2009-08-06
What's gdb? I'm having the same problem with Mozilla, and would probably get the same error code in the other browsers that close randomly.

---

