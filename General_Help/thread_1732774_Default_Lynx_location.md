---
title: "Default Lynx location"
date: 2011-04-18
forum: General Help
---

### Post by mike64485 on 2011-04-18
I'm embarrassed to ask this but...
What is the default location for the _Lynx web browser_ executable? 

Thanks for the help! 

Mike :P

---

### Post by nitstorm on 2011-04-18
i think it should be somewhere in /bin  That's where most of the programs get stored

---

### Post by ihaveapc on 2011-04-18
$ which lynx
/usr/bin/lynx

Hope this helps :)

---

### Post by mike64485 on 2011-04-19
I tried both suggestions. No luck. I tried just searching from root down in */bin, /etc, /sbin*, and */usr/*... where I found this link:

usr/bin/lynx 

which pointed me to this file:

/etc/alternatives/lynx, 

which pointed me to this file:

/usr/bin/lynx.cur,

which is a cursor file, and not executable. The properties page for this file does not point to any other file.

I also found config files and the original downloaded .tar.gzip file.

Further search under /usr/... did not provide any results.

Any other suggestions will be greatly appreciated.

Lynx ver 2.8.8dev.2-1  text-mode browser, Ubuntu 10.04 (lucid)

Thanks again for your help!

Mike

---

### Post by matt_symes on 2011-04-19
Hi

> **mike64485 said:**
> where I found this link:

usr/bin/lynx 

which pointed me to this file:

/etc/alternatives/lynx, 

which pointed me to this file:

Yes you can follow the symlinks, but as you found they point to...

```
matthew@matthew-laptop:~/my_documents/my_tutorials$ readlink -e $(ls  $(which lynx))
/usr/bin/lynx.cur
matthew@matthew-laptop:~/my_documents/my_tutorials$
```


> 
/usr/bin/lynx.cur

which is a cursor file, and not executable.

However...

```
matthew@matthew-laptop:~/my_documents/my_tutorials$ file /usr/bin/lynx.cur
/usr/bin/lynx.cur: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
matthew@matthew-laptop:~/my_documents/my_tutorials$ 
```

```
matthew@matthew-laptop:~/my_documents/my_tutorials$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
matthew@matthew-laptop:~/my_documents/my_tutorials$ 
```

```
matthew@matthew-laptop:~/my_documents/my_tutorials$ dpkg -l | grep lynx
ii  lynx                                  2.8.8dev.2-1                                    Text-mode WWW Browser (transitional package)
ii  lynx-cur                              2.8.8dev.2-1                                    Text-mode WWW Browser with NLS support (development version)
matthew@matthew-laptop:~/my_documents/my_tutorials$ 
```

That is the executable for me.

Kind regards

---

