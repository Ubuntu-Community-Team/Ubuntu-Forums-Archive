---
title: "Why can firefox never load java applets properly on Ubuntu?"
date: 2012-03-18
forum: General Help
---

### Post by alkal0id on 2012-03-18
I'm learning how to make java applets at the moment but its a pain in the *** because I have to boot up a Windows VM just to test them. Ever since I can remember, java applets have given me mad trouble and are responsible for 95% of the every browser crash thats happened to me. Firefox on Windows seems to deal with applets fine. Heres an example:
[http://www.muq.org/~cynbe/java/classes/hello/hello.html](http://www.muq.org/~cynbe/java/classes/hello/hello.html)
I can load that page fine on Windows 7. On Ubuntu, firefox crashes before the page even comes up. In the past, I've noticed that even when I force firefox to shut down after a java applet crashed it, my computer remains really slow and according to the system monitor, the process thats eating up all the memory is java. Theres no process that I've had to manually kill more times than java. I have no idea what the problem is. I recently installed jdk 7 fully which comes with its own firefox plugin. I disabled the IcedTea java plugin and just left the jdk 7 one enabled but I still have the same problem. Half the applets I come across either crash the browser or don't work at all. Some applets, even highly complex ones work perfectly for some reason, whereas in other situations, simple hello world applets crash firefox. Any idea what the problem is and how to fix it?

---

### Post by Subidubi32 on 2012-03-18
Are you using the openJDK or the Oracle Java?

---

### Post by alkal0id on 2012-03-18
Oracle. Initially, I installed OpenJDK but it wasn't working properly so I uninstalled it and got JDK 7 from the oracle website.

---

