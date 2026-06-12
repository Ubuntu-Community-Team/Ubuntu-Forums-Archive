---
title: "Missing zlib module in python"
date: 2010-04-09
forum: General Help
---

### Post by erkswede on 2010-04-09
Hi all

I'm trying to run a backup script in an application which reports the following error message:
> ** An error occurred while performing the backup process. **
Exception -> ['Traceback (most recent call last):\n', '  File "backupdb.py", line 402, in main\n', '  File "wtbackup.py", line 2665, in main\n', '  File "jtfs.py", line 64, in creatercptbackup\n', '  File "jtfs.py", line 253, in makebackup\n', '  File "ziphandler.py", line 1221, in writestr\n', '  File "/home/planders_scratch/76m1/python/../dist/pd/Linux/python/lib/python2.1/zipfile.py", line 163, in __init__\n    raise RuntimeError,\\\n', 'RuntimeError: Compression requires the (missing) zlib module\n']

The application in question is Journyx Timesheet 7.6m1 and it is running on a Ubuntu 9.04. The script works fine in Ubuntu 8.04.

Python 2.1.3 seems to be "bundled" with this app so I'm guessing things get screwed up with different python versions, or something.
The script dumps a database to a file and compresses it, and it seems that the compression doesn't work. That's my guess anyway. From the error message above I gather that a python module is missing?
Any help on this would be appreciated as I have no experience with python.

Kind regards
/erkswede

---

### Post by gmargo on 2010-04-09
Comparing some python filenames on my 8.04 Hardy system:
```

$ ls -l /usr/lib/python2.5/zipfile.py /usr/lib/python2.5/lib-dynload/zlib.so /usr/lib/libz.so.1
lrwxrwxrwx 1 root root    15 Apr 19  2009 /usr/lib/libz.so.1 -> libz.so.1.2.3.3
-rw-r--r-- 1 root root 21648 Jan 20 15:05 /usr/lib/python2.5/lib-dynload/zlib.so
-rw-r--r-- 1 root root 35621 Jan 20 15:04 /usr/lib/python2.5/zipfile.py

```You seem to have a corresponding zipfile.py under your python2.1 directory.  Do you have an associated lib-dynload/zlib.so file?  That's the file that zipfile.py is looking for.  And it uses the /usr/lib/libz shared library to do the actual compression (from the libz1g package.)

---

### Post by erkswede on 2010-04-09
thanks for your reply gmargo

I do have the .../python2.1/lib-dynload/zlib.so file.

I did some reading and tried to do manual import at the python prompt:

```
Python 2.1.3 (#1, Apr 25 2008, 15:28:49)
[GCC 3.2.2 20030222 (Red Hat Linux 3.2.2-5)] on linux2
Type "copyright", "credits" or "license" for more information.
>>> import zlib
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: libz.so.1: cannot open shared object file: No such file or directory

```

I can't see any filed called libz.so.1 in /usr/lib

Tried ldd on the zlib.so:

```
ldd pd/Linux/python/lib/python2.1/lib-dynload/zlib.so
        linux-gate.so.1 =>  (0xf771c000)
        libz.so.1 => not found
        libc.so.6 => /lib32/libc.so.6 (0xf75a9000)
        /lib/ld-linux.so.2 (0xf771d000)

```

regarding the libz1g package, I guess you mean zlib1g? I have the latest version of that anyway. Do I perhaps need an older version of that to run python 2.1?

Out of ideas...

---

### Post by gmargo on 2010-04-09
You are correct, I meant the **zlib1g** package.  It contains /usr/lib/libz.so.1 (Hardy,Intrepid), or /lib/libz.so.1 (Jaunty,Karmic).  Are you sure you have it installed?

---

### Post by erkswede on 2010-04-09
Yep, i'm sure:

```
# apt-get install zlib1g
Reading package lists... Done
Building dependency tree
Reading state information... Done
zlib1g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

```

and I do have the /lib/libz.so.1 file

did a reconfigure as well: dpkg-reconfigure zlib1g
but it didn't make any difference.

---

### Post by gmargo on 2010-04-09
I just noticed the /lib32 stuff - you're running a 32 bit app on a 64 bit install?  I think you need the **lib32z1** package, which provides /usr/lib32/libz.so.1

[http://packages.ubuntu.com/jaunty/lib32z1](http://packages.ubuntu.com/jaunty/lib32z1)

---

### Post by erkswede on 2010-04-09
lib32z1 did the trick, great stuff.

Thanx a lot gmargo, my hero!

---

