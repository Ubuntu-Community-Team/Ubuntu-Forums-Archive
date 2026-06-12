---
title: "Error occurred during initialization of VM"
date: 2006-05-08
forum: General Help
---

### Post by element on 2006-05-08
When launching the Novell Groupwise client I get the following...

Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

When I do a "java -version" here is what I have...

java version "1.4.2_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_11-b06)
Java HotSpot(TM) Client VM (build 1.4.2_11-b06, mixed mode)


Anyone know why I am getting this error and how I can resolve it?
Thanks

---

### Post by ryan-au on 2006-05-09
Check out my HOWTO regarding GroupWise:

[http://www.ubuntuforums.org/showthread.php?t=147278]("http://www.ubuntuforums.org/showthread.php?t=147278")

You generally need to use a specific version of the JRE and link it correctly to your GroupWise install to override the one that ships with it.

I've just got the Public Beta 7.0.1 r4 working with J2RE 1.5 update 06 as noted in the above link.  r4 has new icons on the context menus! :P

Hope that helps ...

---

### Post by element on 2006-05-12
Thanks, that worked!

---

