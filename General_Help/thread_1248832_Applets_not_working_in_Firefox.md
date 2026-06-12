---
title: "Applets not working in Firefox"
date: 2009-08-24
forum: General Help
---

### Post by spyder0101 on 2009-08-24
Using Firefox 3.0.13, Ubuntu 9.04 x64, How do I get applets to work in firefox?

Thanks.

---

### Post by DeMus on 2009-08-24
> **spyder0101 said:**
> Using Firefox 3.0.13, Ubuntu 9.04 x64, How do I get applets to work in firefox?

Thanks.

Applets? You mean plugins or add-ons?

---

### Post by spyder0101 on 2009-08-24
I mean Java applets, as in Java programs running within a browser window.

---

### Post by DeMus on 2009-08-24
> **spyder0101 said:**
> I mean Java applets, as in Java programs running within a browser window.

Did you install Java?
There are several ways to do so, what is the best way at the moment is something I don't know, maybe somebody else can help here.

---

### Post by spyder0101 on 2009-08-24
Yes, here is my java -version
```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)

```

---

### Post by DeMus on 2009-08-24
> **spyder0101 said:**
> Yes, here is my java -version
```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)

```

Sorry, can't help you here.

Please somebody else, give this man a hand.

---

### Post by wolfchri on 2009-08-26
Same problem here, Java applets are not working in Firefox, although I installed the complete OpenJDK packages from the ubuntu-extra meta package.... :(

Test yourself here:

[http://www.java.com/de/download/installed.jsp?detect=jre&try=1](http://www.java.com/de/download/installed.jsp?detect=jre&try=1)

---

### Post by wolfchri on 2009-08-26
Seems to be a well known bug, not fixed for quite some while, rendering Java on Ubuntu useless for normal users:

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705)

Not good :-(

---

### Post by novafluxx on 2009-08-26
> **spyder0101 said:**
> Yes, here is my java -version
```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)

```

You may have Java installed, but you ALSO need the Java plug-in which you can get from the repo's

EDIT: I see you're using OpenJDK...I've had nothing but negative experiences with that, so I can't speak for it

---

### Post by scouser73 on 2009-08-26
Personally, I have had problems with the OpenJDK Runtime Environment, so I have installed **Sun Java 6 JRE** and the **Sun Java 6 Plugin**, which can be found in **Synaptic Package Manager**.

---

