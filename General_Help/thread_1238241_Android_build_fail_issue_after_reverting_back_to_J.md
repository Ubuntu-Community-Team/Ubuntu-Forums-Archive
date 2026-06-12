---
title: "Android build fail issue after reverting back to JDK 5.0"
date: 2009-08-12
forum: General Help
---

### Post by krish24in on 2009-08-12
Hi all,
 
We have ubuntu version 8.04 with JDK 6 (java version "1.6.0_10). We were using the ubuntu server for Android build and build was happening fine. In latest release of Android, its been suggested to revert back to JDK 5. After uninstalling the JDK 6 and installing JDK 5.0, I am getting following error:
 
[FONT=Courier New]You are attempting to build with the incorrect version[/FONT]
[FONT=Courier New]of javac.[/FONT]
 
[FONT=Courier New]Your version is: Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved..[/FONT]
[FONT=Courier New]The correct version is: 1.5.[/FONT]
 
Anyone knows how to fix this? 
 
Please suggest what else i need to do.
 
krish

---

### Post by goo25 on 2009-10-25
this worked for me: 

```
sudo update-java-alternatives -s java-1.5.0-sun
```

depending on your version of java. 

and then type make again a see what happend.

good luck.
Chris

---

### Post by smo0th on 2010-01-26
did that solved the problem?

---

