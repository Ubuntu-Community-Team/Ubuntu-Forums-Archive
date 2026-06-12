---
title: "Sun-Java-6-jre installed but openjdk loaded"
date: 2010-10-28
forum: General Help
---

### Post by jebradley on 2010-10-28
I have both the openjdk-6-jre and sun-java6-jre versions of java installed on my Ubuntu Maverick desktop, with the sun version setup as the default. I was trying to load the web page, [http://w4mq.com](http://w4mq.com), an amateur radio software defined receiver. I can load the page on Firefox run on XP in a VirtualBox machine, but when loaded on Firefox on my Maverick desktop, I wasn't getting any sound with openjdk, so I installed sun's and set it as the default. When I run 'java -version' from the command line, it reports the following:
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)
but on firefox, when loading the above page, it reports 'java version test applet 1.6.0_20' on the page. 

How do I get sun's version to run? I need to get the sound to work.

Thanks.

---

### Post by GregBrannon on 2010-10-28
Item #2 at this link:

[Which Java to use]("https://help.ubuntu.com/community/Java")

---

### Post by gandaran on 2010-10-28
> **jebradley said:**
> I have both the openjdk-6-jre and sun-java6-jre versions of java installed on my Ubuntu Maverick desktop, with the sun version setup as the default. I was trying to load the web page, [http://w4mq.com](http://w4mq.com), an amateur radio software defined receiver. I can load the page on Firefox run on XP in a VirtualBox machine, but when loaded on Firefox on my Maverick desktop, I wasn't getting any sound with openjdk, so I installed sun's and set it as the default. When I run 'java -version' from the command line, it reports the following:
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)
but on firefox, when loading the above page, it reports 'java version test applet 1.6.0_20' on the page. 

How do I get sun's version to run? I need to get the sound to work.

Thanks.
the best way is to remove the icedtea-plugin, you don't need it if you want sun-java for web browser, removing the icedtea-plugin wont affect the rest of openjdk-java packages or you can remove all the openjdk packages if you dont have any application that depends on them.

---

### Post by jebradley on 2010-10-28
Getting rid of the icedtea plugin and replacing it with the sun-java6-plugin took care of the problem of which applet was loaded, but I still don't have any sound.

---

### Post by gandaran on 2010-10-29
> **jebradley said:**
> Getting rid of the icedtea plugin and replacing it with the sun-java6-plugin took care of the problem of which applet was loaded, but I still don't have any sound.
that you will have to fix with sound preferences, maybe something is disabled  or install the pulseaudio gui (sorry I dont remember the apps name)

---

