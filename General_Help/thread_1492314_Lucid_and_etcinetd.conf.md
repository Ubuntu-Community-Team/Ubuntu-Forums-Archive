---
title: "Lucid and /etc/inetd.conf"
date: 2010-05-24
forum: General Help
---

### Post by jdysinger on 2010-05-24
Hello,
 
Has Inetd been updated to something else or has /etc/inetd.conf been changed to a different directory with Ubuntu 10.04?
 
Just curious, I'm was looking to set permissions on /etc/inetd.conf, but cannot find the file. 
 
If I just need to install it, let me know :)

---

### Post by SlidingHorn on 2010-05-24
try /etc/in**i**td.conf

---

### Post by MrSmite on 2010-05-25
I have the same question, but

> **SlidingHorn said:**
> try /etc/in**i**td.conf

isn't really what i'm looking for since init and inetd are two very different animals.

---

### Post by jdysinger on 2010-05-25
> **MrSmite said:**
> I have the same question, but
 
 
 
isn't really what i'm looking for since init and inetd are two very different animals.
 
I did more googling and just determined that the inetd daemon doesn't seem to come with Lucid. I "apt-get install inetutils-inetd" and was able to find /etc/inetd.conf. 
 
Personally though, based on the reading, I may just uninstall it and use xinetd daemon instead. Supposedly its easier to configure and has better security.

---

### Post by SlidingHorn on 2010-05-25
shows how much I know...lol

I'll be perfectly honest, I didn't know there was an inetd. *facepalm*

---

### Post by gmargo on 2010-05-25
While none are installed by default, there are at least four packages available to provide the "inet-superserver" function:
```

$ apt-cache search inet-superserver
openbsd-inetd - The OpenBSD Internet Superserver
xinetd - replacement for inetd with many enhancements
inetutils-inetd - internet super server
rlinetd - gruesomely over-featured inetd replacement

```

---

### Post by scotthuang1989 on 2013-03-30
> **jdysinger said:**
> I did more googling and just determined that the inetd daemon doesn't seem to come with Lucid. I "apt-get install inetutils-inetd" and was able to find /etc/inetd.conf. 
 
Personally though, based on the reading, I may just uninstall it and use xinetd daemon instead. Supposedly its easier to configure and has better security.
Hi, Could you tell me the link of your reading?

---

### Post by oldos2er on 2013-03-30
Best to start a new thread; jdysinger hasn't visited the forums since 2010.

---

