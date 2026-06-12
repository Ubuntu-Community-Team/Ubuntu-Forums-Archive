---
title: "Python Segmentation fault"
date: 2009-10-04
forum: General Help
---

### Post by cong06 on 2009-10-04
Just yesterday I noticed that most programs wouldn't open. Opening them in the terminal just gave: "Segmentation fault"

upon inspection I realized it wasn't binarys, or even perl scripts, but just python scripts. (probably ever since I yanked a thumb drive out of my ubuntu laptop holding python script that was currently running...)

So. I reinstalled python, but python still gave "Segmentation fault"
So I tried installing python2.5 from some deb files I have lying around (long story...bad bandwidth access)

When that failed (some evidence below) I went ahead and just reinstalled python2.6 since that was the version I had initially.

Anyway, here's the mess I'm in:

```

isaac@pfaff:/usr/bin$ sudo aptitude reinstall python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  python2.6 
The following partially installed packages will be configured:
  maximus python2.5-minimal 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/2454kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 125549 files and directories currently installed.)
Preparing to replace python2.6 2.6.2-0ubuntu1 (using .../python2.6_2.6.2-0ubuntu1_i386.deb) ...
Unpacking replacement python2.6 ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up maximus (0.4.8-0ubuntu3) ...
Segmentation fault
dpkg: error processing maximus (--configure):
 subprocess post-installation script returned error exit status 139
Setting up python2.5-minimal (2.5.4-1ubuntu4) ...
Linking and byte-compiling packages for runtime python2.5...
Segmentation fault
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 139
Setting up python2.6 (2.6.2-0ubuntu1) ...
Segmentation fault

Processing triggers for menu ...
Errors were encountered while processing:
 maximus
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.5-minimal (2.5.4-1ubuntu4) ...
Linking and byte-compiling packages for runtime python2.5...
Segmentation fault
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 139
Setting up maximus (0.4.8-0ubuntu3) ...
Segmentation fault
dpkg: error processing maximus (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 python2.5-minimal
 maximus
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

I tested "purge" but of course Python is needed by so many ubuntu programs.

I also found this post: [http://ubuntuforums.org/archive/index.php/t-925852.html](http://ubuntuforums.org/archive/index.php/t-925852.html)
but don't have the bandwidth to wait for a 23MB file (namely valgrind). Is there another tool I could use instead?

---

### Post by cong06 on 2009-10-04
huh. So I tried switching to python2.5 (probably the wrong way...simply by switching the symbolic link to python2.5 instead of 2.6). That failed

I also tried running gdb, which would be a very valid replacement to valgrind if I knew what the output meant:
```

isaac@pfaff:/usr/bin$ gdb python
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/bin/python 
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb7eb66c0 (LWP 4869)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7eb66c0 (LWP 4869)]
0x0805e8ec in PyTokenizer_FromString ()
(gdb) step
Single stepping until exit from function PyTokenizer_FromString, 
which has no line number information.

Program terminated with signal SIGSEGV, Segmentation fault.
The program no longer exists.
(gdb) 

```

---

