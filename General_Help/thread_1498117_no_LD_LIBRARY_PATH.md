---
title: "no LD_LIBRARY_PATH"
date: 2010-05-31
forum: General Help
---

### Post by bouncingwilf on 2010-05-31
I'm having a problem in linking a simple C application - it may be that I'm just getting too old and forgetful or it may be a system bug - either way I'd appreciate a little help.

The appliction in question is a simple program to query and modify an sqlite3 database. Because I need to use the median aggregate function, I can't use standard Sqlite3 binaries. The code itself is ok ( Ive written similar a couple of years ago for a 64bit Hardy system). I'm still using the same box now (amd64bit) but am using Lucid lynx as the OS.

The program compiles fine with:
 gcc -o normalizer normalizer.c  -Wall -W -O2 -Wl,-R/usr/lib -lsqlite3

but the linker returns:
/usr/bin/ld: cannot find -lsqlite3


However, the are definitely copies of the sqlite3.so in both /usr/lib and /usr/64bit/lib

A search of the internet produced a mas of similar bugs on launchpad e.g.
[https://bugs.launchpad.net/ubuntu/+bug/366728](https://bugs.launchpad.net/ubuntu/+bug/366728)

If I do a printenv, there is no LD_LIBRARY_PATH set

question(s)

a) is this the source of my problem or am I missing something simple.

b) is there a "quick fix" such that I can link this app?

Any help much appreciated. 

Bouncingwilf.

---

### Post by Brandon Williams on 2010-06-01
Unless you are using a non-standard library package, you should have no need to set LD_LIBRARY_PATH. If you want to check whether you just have a bad library installation, then export LD_LIBRARY_PATH in the shell instance in which that you are about to run gcc and see whether gcc can link the binary. For libraries installed in /usr/lib, it should not be the case that this helps, since that path should already be part of the standard gcc library search path.

Which versions of libsqlite3* do you have installed? Run 'dpkg -l libsqlite3*' and post the output. On my 10.04 system, I have:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libsqlite3-0   3.6.22-1       SQLite 3 shared library
ii  libsqlite3-dev 3.6.22-1       SQLite 3 development files
```

Both of these have to be installed to build (the -dev package) and run (the -0 package) applications that link against libsqlite3.

---

### Post by bouncingwilf on 2010-06-03
Many thanks, I had omitted to install the development files - entirely my own fault - I must be going senile!.


Bouncingwilf

---

### Post by Emanuele_Z on 2010-06-12
> **Brandon Williams said:**
> Unless you are using a non-standard library package, you should have no need to set LD_LIBRARY_PATH. If you want to check whether you just have a bad library installation, then export LD_LIBRARY_PATH in the shell instance in which that you are about to run gcc and see whether gcc can link the binary. For libraries installed in /usr/lib, it should not be the case that this helps, since that path should already be part of the standard gcc library search path.

Which versions of libsqlite3* do you have installed? Run 'dpkg -l libsqlite3*' and post the output. On my 10.04 system, I have:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libsqlite3-0   3.6.22-1       SQLite 3 shared library
ii  libsqlite3-dev 3.6.22-1       SQLite 3 development files
```

Both of these have to be installed to build (the -dev package) and run (the -0 package) applications that link against libsqlite3.

Hi, apparently exporting LD_LIBRARY_PATH doesn't work anymore in 10.04.
Are you sure about this?
Because I'm trying to test some dev .so and I can't use LD_LIBRARY_PATH anymore to make mplayer load them.

Cheers,

---

