---
title: "Java Problem in Maverick x64"
date: 2011-01-18
forum: General Help
---

### Post by jugs on 2011-01-18
Hello,

I desperately need your help!

I have downloaded [CRON-O-METER 0.9.7]("http://sourceforge.net/projects/cronometer/files/"), and the shell script provided to launch the application. 

I have modified the shell script to change directory to the valid jar file location, otherwise it is the same one found [here]("http://spaz.ca/cronometer/cronometer.sh").

**Shell script:**
> #!/bin/sh

cd "CRONOMETER/lib/"
java -cp cronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.3.jar:cronometer.jar:usda_sr22.jar:crdb_004.jar:docs.jar ca.spaz.cron.CRONOMETER

I have also modified the permissions to allow execution of this shell script. The problem appears to be java based, as when I run it I get the following error.


**Error:**
> Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/swingx/JXBusyLabel
	at ca.spaz.cron.CRONOMETER.main(CRONOMETER.java:584)
Caused by: java.lang.ClassNotFoundException: org.jdesktop.swingx.JXBusyLabel
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 1 more

I would greatly appreciate some support as I cannot function without this application and I don't want to run it in wine when it should work well natively.

Also, I've tested this with both the latest openjdk-6 then removed it and all related plugins, and tested with the latest sun-java packages. They both result in the exact same error..

Thanks in advance!

---

### Post by lykeion on 2011-01-18
Well. I downloaded this and tried unsuccessfully to run it. The NoClassDefFoundError: org/jdesktop/swingx/JXBusyLabel is because it cannot find the swingx-0.9.3.jar. And browsing through the extracted files I couldn't find it either.

However if you download the MacOS X version you'll find the required jar libraries included and it runs successfully. So this is my solution to you (remember Java applications should be OS independant).

---

### Post by jugs on 2011-01-18
Awesome! Thank you very much!!

For the record, fitday.com is CRAP. Now I can say that openly, as I have the solution :)

I'm going to email the developer and mention this to him, as he is working on a ppa.

---

