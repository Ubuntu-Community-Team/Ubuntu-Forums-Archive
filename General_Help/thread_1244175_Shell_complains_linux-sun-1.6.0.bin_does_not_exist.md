---
title: "Shell complains linux-sun-1.6.0.bin does not exist"
date: 2009-08-19
forum: General Help
---

### Post by keshava.mp on 2009-08-19
I am trying to install Symantec agent on ubuntu server 9.04. 

Agent$ ls -l linux-sun-1.6.0.bin
-rwxrwxrwx 1 praveen praveen 34294452 2007-03-02 04:18 linux-sun-1.6.0.bin


Agent$ file linux-sun-1.6.0.bin
linux-sun-1.6.0.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped


Up to this it is fine, but when I try to execute the file,

Agent$ sudo ./linux-sun-1.6.0.bin -o
sudo: unable to execute ./linux-sun-1.6.0.bin: No such file or directory

I ran a fsck also, it did not return any errors, but problem continues. 

Any help will be appreceiated.

---

### Post by Bachstelze on 2009-08-19
Are you running the 64 bit version of Ubuntu?

---

### Post by keshava.mp on 2009-08-21
> **HymnToLife said:**
> Are you running the 64 bit version of Ubuntu?

Yes. Here is the output:
$ uname -a
Linux syslogng.hpcl.co.in 2.6.28-14-server #47-Ubuntu SMP Sat Jul 25 02:03:55 UTC 2009 x86_64 GNU/Linux

---

