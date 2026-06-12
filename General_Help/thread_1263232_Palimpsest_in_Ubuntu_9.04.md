---
title: "Palimpsest in Ubuntu 9.04"
date: 2009-09-10
forum: General Help
---

### Post by grubster on 2009-09-10
can anyone tell me if you can install Palimpsest in Ubuntu 9.04 64

---

### Post by realloc on 2009-11-11
Bump.  I want this too.  64-bit is essential.  (Who still uses 32-bit anyway?)

I'm gonna try it out on my Ubuntu 9.04 RAID6 server.

---

### Post by mechro on 2009-11-11
List of debian packages to install are here...

[http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html](http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html)

The links seem to be out of date but if you go to the parent directory of the "404 Not Found" page you'll be in the relevant debian folder where you can choose 64 bit stuff.

I use 32-bit! :p

---

### Post by raix on 2009-11-20
That's not working for me.
When trying to install the libgdu-gtk0_2.28.1-1_amd64.deb package dpkg complains that it needs libglib2.0-0 (>= 2.22.0) but 2.20.1-0ubuntu2.1 is installed. Same for libgtk.2.0-0.

Any ideas?

---

### Post by realloc on 2009-11-27
I have the same problem.  Here are the errors from just libgdu-gtk0.


```
root@dereks-laptop:~/Palimpsest# dpkg -i libgdu-gtk0_2.28.1-2_amd64.deb 
(Reading database ... 208151 files and directories currently installed.)
Preparing to replace libgdu-gtk0 2.28.1-2 (using libgdu-gtk0_2.28.1-2_amd64.deb) ...
Unpacking replacement libgdu-gtk0 ...
dpkg: dependency problems prevent configuration of libgdu-gtk0:
 libgdu-gtk0 depends on libatasmart4 (>= 0.13); however:
  Package libatasmart4 is not installed.
 libgdu-gtk0 depends on libglib2.0-0 (>= 2.22.0); however:
  Version of libglib2.0-0 on system is 2.20.1-0ubuntu2.1.
 libgdu-gtk0 depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.16.1-0ubuntu2.
dpkg: error processing libgdu-gtk0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgdu-gtk0
root@dereks-laptop:~/Palimpsest#
```

I also tried to install libatasmart4 (and also libatasmart0), and that package is not found:

```
root@dereks-laptop:~/Palimpsest# apt-get install libatasmart4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libatasmart4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libatasmart4 has no installation candidate
root@dereks-laptop:~/Palimpsest# 
```


I guess I'll be forced to upgrade to 9.10 to get this app... not something I really want to do yet.  :(

(The 9.04 nmap package is also broken.  I guess now I have two reasons to upgrade.)

---

### Post by leorolla on 2010-05-11
I recommend Jaunty over Karmic...

Actually I used Karmic for very long, upgraded to Lucid, and I am seriously considering an "upgrade" to Jaunty.

Use gdebi-gtk instead of dpkg -i ;-)

---

