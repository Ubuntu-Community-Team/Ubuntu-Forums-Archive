---
title: "How do I reconfigure php5?"
date: 2009-08-19
forum: General Help
---

### Post by lorderico on 2009-08-19
I have the problem described here: [http://oscartheduck.wordpress.com/2007/04/19/applicationx-httpd-php-downloading-instead-of-being-served-by-wordpress-on-freebsd/](http://oscartheduck.wordpress.com/2007/04/19/applicationx-httpd-php-downloading-instead-of-being-served-by-wordpress-on-freebsd/)

The solution given is to reconfigure php.  However, the instructions to do that are not clear.  How do I reconfigure php?

Thanks,

Eric

---

### Post by cariboo on 2009-08-19
Make sure you have libapache2-mod-php5 installed, that should solve your problem. The package is in the repositories.

---

### Post by lorderico on 2009-08-19
libapache2-mod-php5 is installed and at the newest version.  I am still having the problem.

---

### Post by lorderico on 2009-08-19
I found out that this was only happening on my PC.  I then restarted my my PC, and the problem was fixed.  That was only after re-installing the entire operating system, however....

Eric

---

### Post by oscartheduck on 2009-11-07
Hey buddy,

the solution on *FreeBSD* is to reconfigure the php5 port, but that's because package management on FreeBSD is different to Ubuntu. The problem I was identifying and solving was that libphp5.so, a dynamic library, wasn't installed automatically because of a mistake I'd made in the order I'd installed things in. 

If you figured you were fraught with the same issue, the thing to do is find out what package provides that library and install it. Cariboo2007 correctly identified this as libapache2-mod-php5.

If you're still not getting off to a flying start, then check your logs, think for a while and ponder what might be causing the issue. 

The first step is to understand the issue. What's happening is that your files are being delivered by apache instead of being interpreted by the php module and the output of that delivered. So the solution is one of several things.

First, you can visit the apache website and start reading up on documentation for how to verify that a module, in this case the php module, is actually installed and working correctly. You'll learn about httpd.conf and the like, which is really, really, really useful information.

Second, you can visit these forums or the IRC channel and try and have an expert help you solve the issue.

Third, you can reinstall and hope everything works this time.

Whilst the third is a fast route to solving things, you'll see that the first two would give you a better understanding of your system. A package somewhere was misconfigured, and simply correcting the misconfiguration would've got you where you needed to be.

---

