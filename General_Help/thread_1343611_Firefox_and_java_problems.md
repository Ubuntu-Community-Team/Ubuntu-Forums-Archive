---
title: "Firefox and java problems"
date: 2009-12-02
forum: General Help
---

### Post by claracc on 2009-12-02
Hallo, i have the following problem.

Since i upgraded from jaunty to karmic i have java 6 sun installed: version 1.6.0_15 in /usr/lib/jvm (it was downgraded automatically by synaptic i think, because in jaunty version was 1.6.0_16).

As i couldn't see applets clicking on hyperlinks inserted in openoffice 3.1 which was configured to use jre version 1.6.0_15 (they appeared as grey squares) but i could see these same applets in firefox 3.5 using this plugin, I uninstalled version 1.6.0_15 and installed version 1.6.0_17-b04 following the advice in this thread:[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java).

I am positive I deleted old java version, I configured the new one in openoffice and I can see the applets from there.

Now i have noticed that version 1.6.0_15 has reappeared in my system (i haven't installed conciously) and have the two versions,  but if I write java -version in xterm I obtain: 
java version "1.6.0_17"
Java(TM) SE Runtime Environment (build 1.6.0_17-b04)
Java HotSpot(TM) Server VM (build 14.3-b01, mixed mode).

So, when I see an applet in firefox 3.5 the sun java console running says:
Java Plug-in 1.6.0_15
Usar versión JRE 1.6.0_15-b03 Java HotSpot(TM) Server VM
Directorio local del usuario = /home/clara.

I have the two plugins in firefox: 1.6.0_15 and 1.6.0_17

Since yesterday I cannot see some embeded videos in web page BBC news, when i click on them firefox frezzes and try loading them but never load, only
ads before videos.

Sometimes appears an advice that some java script is creating problems.

Also web pages with java applets in firefox freezes and cause a high consume of CPU

¿Is it related to java version i have?. ¿I have to delete java 1.6.0_17 aqnd stay with 1.6.0_15?, but in this way applets cannot be seen from openoffice.

Any idea is welcome, thanks in advance.

---

### Post by zooounds on 2010-03-24
I have the same issue. Different version in terminal and firefox.
I have only one installed version and java applets does not work at all.

---

