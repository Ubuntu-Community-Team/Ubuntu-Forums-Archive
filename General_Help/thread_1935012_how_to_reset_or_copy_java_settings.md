---
title: "how to reset or copy java settings?"
date: 2012-03-03
forum: General Help
---

### Post by lvm on 2012-03-03
I've got two seemingly identical machines, both running kubuntu-32 11.10 with openjdk-6 and icedtea upgraded up to date. Most of the sites which use java run well on both machines but there is one that works only on one (the 'good' one). I tried copying all I could find related to java and java plugin from the 'good' to the 'bad' machine, namely

/etc/icedtea-web
/etc/java
/etc/java-6-openjdk
/etc/ssl/certs/java
~/.icedtea

But it didn't change a thing. What else am I missing? (and no, I didn't forget to delete everything from these folders before copying) How can I make java on the 'bad' machine behave exactly as on the 'good' one? It may have something to do with applet security - on the site in question security is a mess, on the 'good' machine I get no less than three warnings about bad certificates, mixture of signed and unsigned code etc - but then it works, on the 'bad' one - just one warning, and it doesn't work.

I cannot discolose the site, applet in question is the properJavaRDP if it helps.

---

