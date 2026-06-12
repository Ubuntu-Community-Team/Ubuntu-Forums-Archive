---
title: "Segmentation faults from random programs"
date: 2011-03-02
forum: General Help
---

### Post by jurth on 2011-03-02
Hey experts

I have an annoying problem with Ubuntu 10.10 64bit. I made a clean installation of Ubuntu on my LG P310 laptop and I'm using the Nvidia proprietary driver. 
The problem is that I get segmentation faults from random program after a while of usage. Examples of programs are Thunderbird, Synaptic, apt-get and tap crashes in Chromium (which I would think is segmentation faults). It would seem like a underlying library is causing the faults. The problem disappear after a reboot, the faults might only occur after a wakeup from suspend, I'm not sure about that at the moment.
I can't figure out what triggers these faults, and I don't know how to do error tracing in this case. Can anybody help me the the search of a solution?

/Jonas

---

### Post by Mariane on 2011-03-02
Try running all your programs from the command line. For example instead of clicking to launch firefox you open a terminal and type "firefox" (without quotation marks). 

This way, if these are SIGSEGV (segmentation faults) it will be written in the terminal window after the crash. Post the error messages here or look them up online. 

Mariane

---

### Post by jurth on 2011-03-02
> **Mariane said:**
> Try running all your programs from the command line. For example instead of clicking to launch firefox you open a terminal and type "firefox" (without quotation marks). 

This way, if these are SIGSEGV (segmentation faults) it will be written in the terminal window after the crash. Post the error messages here or look them up online. 


Yep, this is what I did to figure out it was segmentation faults, however no more information is outputted than: "Segmentation fault". It might be possible to get more information via a debugger like gdb, but I have not experience with that, so I don't know if this is the way to go, or there might be other ways.

/Jonas

---

### Post by jurth on 2011-03-10
*Bump*

---

### Post by jurth on 2011-03-11
Hi again

I tried to do some debugging to solve this problem, and i might have been doing all wrong, but here we go. Thunderbird just started crashing so with a bit of from from here: [https://developer.mozilla.org/en/Debugging_Mozilla_on_Linux_FAQ](https://developer.mozilla.org/en/Debugging_Mozilla_on_Linux_FAQ), tried to run Thunderbird with the gdb like this from the command line:

```

jonas@neptun:~$ ulimit -c unlimited
jonas@neptun:~$ cd /usr/lib/thunderbird-3.1.8
jonas@neptun:/usr/lib/thunderbird-3.1.8$ export LD_LIBRARY_PATH=.
jonas@neptun:/usr/lib/thunderbird-3.1.8$ ./thunderbird -g -d gdb
./run-mozilla.sh -g -d gdb ./thunderbird-bin
MOZILLA_FIVE_HOME=.
  LD_LIBRARY_PATH=.:./plugins:.
DISPLAY=:0.0
DYLD_LIBRARY_PATH=.:.
     LIBRARY_PATH=.:./components:.
       SHLIB_PATH=.:.
          LIBPATH=.:.
       ADDON_PATH=.
      MOZ_PROGRAM=./thunderbird-bin
      MOZ_TOOLKIT=
        moz_debug=1
     moz_debugger=gdb
/usr/bin/gdb ./thunderbird-bin -x /tmp/mozargs.74E2kC
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/lib/thunderbird-3.1.8/thunderbird-bin...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/lib/thunderbird-3.1.8/thunderbird-bin 
[Thread debugging using libthread_db enabled]
[New Thread 0x7fffe81ff700 (LWP 7971)]
[New Thread 0x7fffe75ff700 (LWP 7972)]
[New Thread 0x7fffe6bf4700 (LWP 7973)]
[New Thread 0x7fffe63f3700 (LWP 7974)]
[New Thread 0x7fffe55ff700 (LWP 7975)]
[New Thread 0x7fffe49ff700 (LWP 7976)]
[New Thread 0x7fffe37ff700 (LWP 7977)]
[New Thread 0x7fffe2cff700 (LWP 7978)]
[Thread 0x7fffe37ff700 (LWP 7977) exited]
[New Thread 0x7fffe37ff700 (LWP 7979)]
[New Thread 0x7fffdb21a700 (LWP 7980)]
[New Thread 0x7fffdaa19700 (LWP 7981)]
[New Thread 0x7fffd98ff700 (LWP 7982)]
[New Thread 0x7fffd90fe700 (LWP 7983)]

Program received signal SIGSEGV, Segmentation fault.
0x000000000057410a in ?? ()
(gdb) 

```
^ so that was the output after the crash, I was kind of hoping for some stacktrace like stuff, am I doing it all wrong? 

I would really appreciate some help here, I'm getting so despreate that I'm thinking about swiching to a other distribution (I have tried to reinstall, and Ubuntu 10.04 did not give me any problems).

/Jonas

---

### Post by jurth on 2011-03-22
Found out it was a memory error. I ran the memory test, which gave me a lot of errors. Removed one of the memory modules, and the errors where gone.

/Jonas

---

