---
title: "Can I install *.rpm packages? What to prefer Java.rpm or through Repository?"
date: 2011-09-29
forum: General Help
---

### Post by pstein on 2011-09-29
Assume I have a *.rpm package downloaded.
 
How can I install it under Ubuntu?
 
Example Java J2SE from 
 
[http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html](http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html)
 
If I have to decide how to install Java. Either through 
1) downloaded *.rpm package 
or
2.) apt-get install command     from (additional Canonical) Repository
 
What should I prefer?
 
Peter

---

### Post by haqking on 2011-09-29
> **pstein said:**
> Assume I have a *.rpm package downloaded.
 
How can I install it under Ubuntu?
 
Example Java J2SE from 
 
[http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html](http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html)
 
If I have to decide how to install Java. Either through 
1) downloaded *.rpm package 
or
2.) apt-get install command     from (additional Canonical) Repository
 
What should I prefer?
 
Peter

you can use alien to convert packages.


```
sudo apt-get intall alien
```

i think there is a GUI front end somewhere too

---

### Post by CatKiller on 2011-09-29
You should always prefer the repositories if a package is available there. It makes dependencies and updates much easier. As haqking says, you can use alien if the only option is an RPM.

---

