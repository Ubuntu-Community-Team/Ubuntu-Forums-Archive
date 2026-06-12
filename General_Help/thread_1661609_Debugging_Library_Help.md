---
title: "Debugging Library Help"
date: 2011-01-06
forum: General Help
---

### Post by syedr on 2011-01-06
I was dumping instructions from a simple hello world program today using Pin, a dynamic instrumentation tool.

An instruction I'm interested in debugging is from the following source: /lib/ld-linux.so.2:.text+0x1b3e.

To get more information about this source, my goal was to install a debug version of libc6 and change LD_LIBRARY_PATH to point to it, hoping for Pin to discover more e.g. function name for the instruction.  

I need to get hello world to somehow use the debug libc library, so that I can glean more (symbolic) information about the instruction source above. I have been stuck on trying to get this done, and I would really appreciate any help!

Here’s what I did:

**Step 1:**
I installed the package libc6-dbg.

**Step 2:**
I checked to see that I now have the directory /usr/lib/debug/ present.
Previously, it was not there.

*Possible Issue:* 
The directory doesn’t contain libc.so.6. Is it supposed to? See below:

```
/usr/lib/debug$ ls
lib  lib64  sbin  usr

/usr/lib/debug/lib$ ls
ld-2.12.1.so               libcidn-2.12.1.so   libmemusage.so           libnss_files-2.12.1.so    libpcprofile.so       libSegFault.so
libanl-2.12.1.so           libcrypt-2.12.1.so  libnsl-2.12.1.so         libnss_hesiod-2.12.1.so   libpthread-2.12.1.so  libthread_db-1.0.so
libBrokenLocale-2.12.1.so  libdl-2.12.1.so     libnss_compat-2.12.1.so  libnss_nis-2.12.1.so      libresolv-2.12.1.so   libutil-2.12.1.so
**libc-2.12.1.so**             libm-2.12.1.so      libnss_dns-2.12.1.so     libnss_nisplus-2.12.1.so  librt-2.12.1.so       tls

```

What’s up with the weird name (libc-2.12.1.so), by the way? 
Shouldn't there be a libc.so.6 somewhere? Do I need to create some symbolic links?

**Step 3:**
I found out that in Ubuntu, you can’t change LD_LIBRARY_PATH directly – instead, I believe you have to edit the files in /etc/ld.so.conf.d/*

My  /etc/ld.so.conf file is:
```
include /etc/ld.so.conf.d/*.conf

```
The original file /etc/ld.so.conf.d/libc.conf was:
```
# libc default configuration                                                                                                                                            
/usr/local/lib  
```

I changed it to:
```
# libc default configuration                                                                                                                                            
# /usr/local/lib  
/usr/lib/debug/
```

**Step 4:**
I found out you have to do ‘sudo ldconfig’ to push these changes made to the configuration files.
I typed that in the terminal.

**Step 5:**
I created hello world again (with the –g flag in any case). 
```
gcc -g -o hello_world hello_world.c
```

Step 6:
```
$ ldd helloworld
linux-gate.so.1 =>  (0x0033a000)
libc.so.6 => /lib/libc.so.6 (0x0065a000)
/lib/ld-linux.so.2 (0x00560000)
``` 

Here, the debug version of the library is not being used…

[I]Note:
[/I]I tried:
```
gcc -L /usr/lib/debug/lib/libc-2.12.1.so -o hello_world hello_world.c
```

But this didn’t change the output of ldd.

Version information: 
```
uname -a:
Linux ubuntu 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

```

Please help; I would really appreciate it! I'm pretty desperate, and have been stuck on this for a while. I need to get hello world to link with the debug version of libc, so that I can get Pin to provide more information about /lib/ld-linux.so.2:.text+0x1b3e.

---

