---
title: "Why can't I execute these files?"
date: 2010-05-04
forum: General Help
---

### Post by LifeOnMars on 2010-05-04
I'm having trouble printing with CUPS.  Turns out that none of the binaries under /opt/OpenPrinting-Gutenprint can be executed.  Witness:

root$ cd /opt/OpenPrinting-Gutenprint/bin
root$ ./cups-calibrate
bash: ./cups-calibrate: Permission denied
root$ ldd ./cups-calibrate
/usr/bin/ldd: line 117: ./cups-calibrate: Permission denied
root$ file ./cups-calibrate
./cups-calibrate: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.15, dynamically linked (uses shared libs), not stripped
root$ uname -a
Linux ubuntu3 2.6.27-14-server #1 SMP Mon Aug 31 13:57:10 UTC 2009 i686 GNU/Linux
root$ ls -l ./cups-calibrate
-rwxr-xr-x 1 root root 26118 2010-02-25 10:59 ./cups-calibrate*
root$ strings ./cups-calibrate | grep '\.so'
/lib/ld-lsb.so.3
libpthread.so.0
libcrypt.so.1
libz.so.1
libcupsimage.so.2
libm.so.6
libc.so.6
root$ mount -l
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro) []
/dev/sda6 on /usr type ext3 (rw,relatime) []
/dev/sda12 on /opt type ext3 (rw,relatime) []
/dev/sda7 on /var type ext3 (rw,relatime) []
securityfs on /sys/kernel/security type securityfs (rw)
...
root$ cp ./cups-calibrate /usr/bin/cups-calibrate-TMP
root$ ldd /usr/bin/cups-calibrate-TMP
/usr/bin/ldd: line 117: /usr/bin/cups-calibrate-TMP: Permission denied
root$  /usr/bin/cups-calibrate-TMP
bash: /usr/bin/cups-calibrate-TMP: Permission denied

Any ideas as to why I can't execute this file?  Any other suggestions to try?  The libs in the output from `strings` all exist and respond OK to ldd.

---

### Post by darolu on 2010-05-04
It seems like the file system is in read-only mode, probably there was an error at mounting so it forced it in read-only mode (judging by your mounting options) or the inode is corrupted. If you can stop the server for a bit, try re-mounting the hard drive and see if it works, I had a similar problem with mine (I couldn't even "touch" inside /usr/bin) and restarting to mount the FS back solved it.

---

### Post by uRock on 2010-05-04
have you tried ```
chmod +x cups-calibrate
``` before trying to run it?

---

### Post by Wim Sturkenboom on 2010-05-04
> **uRock said:**
> have you tried ```
chmod +x cups-calibrate
``` before trying to run it?If you go carefully through the opening post

> 
root$ ls -l ./cups-calibrate
-rw**[COLOR="Red"]x[/COLOR]**r-**[COLOR="Red"]x[/COLOR]**r-**[COLOR="Red"]x[/COLOR]** 1 root root 26118 2010-02-25 10:59 ./cups-calibrate*

---

### Post by uRock on 2010-05-04
> **Wim Sturkenboom said:**
> If you go carefully through the opening post
That's not the same.

---

### Post by Wim Sturkenboom on 2010-05-04
Can you explain? I'm obviously missing something ;)

---

### Post by LifeOnMars on 2010-05-04
> **darolu said:**
> It seems like the file system is in read-only mode, probably there was an error at mounting so it forced it in read-only mode (judging by your mounting options) or the inode is corrupted. 

Actually, the filesystem is read-write (and I don't understand why that would matter anyway?).  Here's something I did to verify this:

root$ cp /bin/df /opt/OpenPrinting-Gutenprint/bin/df-TMP
root$ /opt/OpenPrinting-Gutenprint/bin/df-TMP --version
df (GNU coreutils) 6.10
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Written by Torbjorn Granlund, David MacKenzie, and Paul Eggert.

Anything else I can try?

---

### Post by LifeOnMars on 2010-05-04
By the way, **none** of the binaries under /opt/OpenPrinting-Gutenprint can be executed, even though they all have the execute bits set and the `file` command says that they are executables.  I'm using cups-calibrate as the simplest example (it's only 26k).

Interesting mystery, no?

---

