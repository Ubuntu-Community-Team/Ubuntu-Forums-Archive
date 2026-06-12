---
title: "tools.jar missing"
date: 2009-07-08
forum: General Help
---

### Post by babbar.ankit on 2009-07-08
I have installing dspace:
Getting an error :Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
 I got to know some how that it is error associated with j2dk

How to rectify it?

$ sudo apt-get install sun-java6-jre

$ sudo apt-get install sun-java6-jdk

I have already executed the above two commands but getting the same error..
Help!

---

### Post by babbar.ankit on 2009-07-08
Plz rply asap

---

### Post by bduhbya on 2010-11-15
Try:

```
sudo aptitude install openjdk-6-jdk
```

I had the same issue and this corrected it for me.

---

