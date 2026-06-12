---
title: "Library for communicating with Iphone doesnt work"
date: 2011-04-11
forum: General Help
---

### Post by _Aries_ on 2011-04-11
Hello,

I've been trying to connect my iphone to my ubuntu 10.10, and it doesnt want to install the library.

I tried through the terminal, (sudo apt-get dist-upgrade) and I tried the update built into ubuntu and it still doesnt work.

Anyone know whats wrong?

---

### Post by _Aries_ on 2011-04-14
I have itunes installed, could that be causing the problem?


How do I uninstall itunes? without deleting .wine

---

### Post by nothingspecial on 2011-04-14
I don't think it works with the very latest iphone firmware yet.

When it does, don't upgrade your iphone in iTunes until you know for sure that it works.

We're always one or 2 steps behind ;)

---

### Post by _Aries_ on 2011-04-15
iOS 4.2.1? Thanks for the reply though. My problem is that the actual library does not want to install itself. 

In my Update Manager, I have the Library for communicating with the iPhone and iPod Touch. When I try to install it, I get an error:

"The installation or removal of a software package failed." 


installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 226864 files and directories currently installed.)
Preparing to replace libimobiledevice1 1.0.1-1 (using .../libimobiledevice1_1.0.6-1ubuntu1~maverick1_i386.deb) ...
Unpacking replacement libimobiledevice1 ...
dpkg: error processing /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~maverick1_i386.deb (--unpack):
 trying to overwrite '/usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi', which is also in package libimobiledevice0 0.9.7-1ubuntu1
No apport report written because MaxReports is reached already
Processing triggers for hal ...
Regenerating hal fdi cache ...
Errors were encountered while processing:
 /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~maverick1_i386.deb

---

### Post by bturig on 2011-04-28
I have exact same issue. I would be interested if there is a solution.

---

