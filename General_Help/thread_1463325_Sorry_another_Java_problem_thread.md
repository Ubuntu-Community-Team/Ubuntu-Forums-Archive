---
title: "Sorry another Java problem thread"
date: 2010-04-26
forum: General Help
---

### Post by Diverted Income on 2010-04-26
I am running the netbook remix 9.10. I have an SSL VPN box that I need to connect to. I can't seem to get Java running correctly in Firefox to make it work. It always says I need to update Java.
Here is the version 
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)

What am I missing???
Thanks

---

### Post by Yellow Pasque on 2010-04-26
Get the java6-u20 .debs from here:
[http://archive.canonical.com/pool/partner/s/sun-java6/](http://archive.canonical.com/pool/partner/s/sun-java6/)
You need the -bin -jre and -plugin .deb's at minimum.

Once you have them, cd to wherever you donwloaded them to and:
```
sudo dpkg -i sun-java6*
```

---

### Post by Diverted Income on 2010-04-26
Thanks, I am closer. Now I am getting dependency errors ????

---

### Post by Diverted Income on 2010-04-27
New errors now:

Setting up sun-java6-fonts (6.20dlj-1ubuntu3) ...

Errors were encountered while processing:
 sun-java6_6.20dlj-1ubuntu3.diff(2).gz
 sun-java6_6.20dlj-1ubuntu3.diff.gz
 sun-java6_6.20dlj.orig.tar.gz


Any thoughts?

---

### Post by Diverted Income on 2010-04-28
What am I missing?
Thanks!

---

### Post by wojox on 2010-04-28
This is what I use to install Java [http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY](http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY)

---

### Post by Diverted Income on 2010-04-28
Great! I will try it and report back. Thanks!

---

### Post by lovinglinux on 2010-04-28
> **Diverted Income said:**
> Great! I will try it and report back. Thanks!

+1 for that tutorial.

All users that I recommended it were able to make java work.

---

### Post by Diverted Income on 2010-04-30
Hmm. Still doesnt work. still says I need to update Java. It does show that I have V6 release 20 running though??

---

