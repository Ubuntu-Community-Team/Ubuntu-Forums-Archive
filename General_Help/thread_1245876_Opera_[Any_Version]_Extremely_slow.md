---
title: "Opera [Any Version] Extremely slow"
date: 2009-08-21
forum: General Help
---

### Post by jacksterson on 2009-08-21
Every time I install Opera (after uninstalling/purging of course) it runs very slow, and I've found many topics with similar problems but not as specific as mine, well as general.  Its not flash, its not java, all the pages just take 30-40 seconds to start even loading.

Can someone please help me?  I really want to try Opera

I'm running Jaunty Jackalope 9.04, btw.

---

### Post by nikhilk on 2009-08-21
> **jacksterson said:**
> Every time I install Opera (after uninstalling/purging of course) it runs very slow, and I've found many topics with similar problems but not as specific as mine, well as general.  Its not flash, its not java, all the pages just take 30-40 seconds to start even loading.

Can someone please help me?  I really want to try Opera

I'm running Jaunty Jackalope 9.04, btw.

Sorry, this might not be the solution you are looking for but I suggest try [Opera 10 beta 3]("http://www.opera.com/browser/download/?os=linux-i386&ver=10.00b3&local=y") if you haven't already. It is very stable and has been working perfectly fine for me as my primary browser.

I have given a i386 link, if you are using a 64 bit installation [this]("http://www.opera.com/browser/download/?os=linux-x86-64&ver=10.00b3&local=y") is the link.

---

### Post by jacksterson on 2009-08-21
I get this error after trying to install with debian.

Error: Dependency is not satisfiable: libqt3c102-mt (>= 3:3.2.1)

---

### Post by jacksterson on 2009-08-21
So am I doomed to use firefox and never opera, or what?  i just tried updating my kernel to the latest and adding ipv6.disable 1 or whatever, and it made me lose all my connections,  I had to switch back to my last one.

Why is it so difficult to get a program thats already compiled for Jaunty to freakin work!? >:(

---

### Post by jacksterson on 2009-08-21
Bump.  Nobody has any solutions?

---

### Post by JudahXIII on 2009-08-21
> **nikhilk said:**
> Sorry, this might not be the solution you are looking for but I suggest try [Opera 10 beta 3]("http://www.opera.com/browser/download/?os=linux-i386&ver=10.00b3&local=y") if you haven't already. It is very stable and has been working perfectly fine for me as my primary browser.

I have given a i386 link, if you are using a 64 bit installation [this]("http://www.opera.com/browser/download/?os=linux-x86-64&ver=10.00b3&local=y") is the link.


Hey buddy,I tried Opera10beta3, but when I installed it, show me "libqt3c102-mt (>= 3:3.2.1)" too, any idea ? Thanks...

---

### Post by jacksterson on 2009-08-22
Theres really no place else to go, guys, I'm a newb at Ubuntu, and this is depressing me very much so :/

---

### Post by nikhilk on 2009-08-24
It seems that the libqt3-mt package is the one you need for Opera although it is named differently viz. libqt3c102-mt which is no longer present in Ubuntu repositories.

Try installing it as mentioned in [this]("http://ubuntuforums.org/showthread.php?t=1244455") thread and see how it goes.

---

### Post by longtom on 2009-08-24
I installed without a hitch in 8.04 and runs beautifully.

Another Jaunty problem?  Or Opera using the wrong (old) libraries?

---

### Post by jacksterson on 2009-08-25
It didn't work, I tried installing on intrepid as well, same problem.

---

### Post by jacksterson on 2009-08-26
bump

---

### Post by eMJayy on 2009-09-02
I'm not an expert in this area, but I just found what seems to be a solution to this problem.

I've had a similar problem for several months. I'm primarily a FF user so I didn't bother to really do anything about it until today. Basically, what I discovered is that the issue has to do with DNS lookups using IPv6. It's a new protocol that has not been implemented very much as yet. However, it's been made the default in Ubuntu and Opera's having a problem dealing with it. 

When Opera does a DNS lookup, it queries using IPv6 and then gets an error...then it eventually repeats the query in IPv4 and gets the info it's looking for. Unfortunately, this whole process seems to be taking a lot of time for the Opera browser, and it makes some pages take forever to begin loading. The other browsers aren't affected in this way by having IPv6 as default. There's no way to disable the use of IPv6 in Opera (there is in FF) but what I found was that using OpenDNS for DNS lookups instead of the default DNS settings seems to work - i haven't had any problems with Opera since I changed the settings an hour ago. 

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

