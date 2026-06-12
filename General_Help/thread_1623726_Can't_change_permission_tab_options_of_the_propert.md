---
title: "Can't change permission tab options of the properties of any .exe file"
date: 2010-11-16
forum: General Help
---

### Post by s.shawky on 2010-11-16
After i upgraded to Ubuntu 10.10 i can't change the permission options of any exe file so i couldn't allow executing file as a program except when i move this file to desktop (/ partion) 
so how can i allow executing file as a program without moving it
and how can i change my file permission

---

### Post by mc4man on 2010-11-17
Don't bother... - .exe's don't need to have x bit set. This behavior is the result of an ill-advised security policy.

Numerous ways around, one simple one - 

Right click on any .exe -> properties -> open with -> add -> use a custom command. For command use just - 
 wine
After that a d. left click on any .exe will open directly with wine, no need to set permission. Also you'll see wine as a choice in the r. click on any .exe (vs. wine windows program loader

---

### Post by s.shawky on 2010-11-17
thank you this solved the problem for .exe when i choose winebrowser instead of (wine windows programs loader) but what about .jar files which work with Java it asks me to allow executing file as program

---

### Post by mc4man on 2010-11-17
> but what about .jar files

Several ways - don't have any .jar's on hand to test
you could automount that/those partitions, depending on the fstab entry **all** .exe, text files and probably .jar would be marked exec - don't like that solution too much

Try the same idea as above, for custom command use (Assuming you're using openjdk-6-jre
```
/usr/lib/jvm/java-6-openjdk/bin/java -jar
```
will show up as java in context menu  - screen as java

or
Globally for all users
Open the .desktop for java and edit the Exec= to remove the cautious launcher from lauch command

```
gksudo gedit /usr/share/applications/openjdk-6-java.desktop
```
change the line
Exec=cautious-launcher %f /usr/lib/jvm/java-6-openjdk/bin/java -jar
to
Exec=/usr/lib/jvm/java-6-openjdk/bin/java -jar

You could do the above but just with a local version of the .desktop, seen in screen as OpenJDK Java Free 6 Runtime, only available to you (basically the same as the custom command

---

### Post by s.shawky on 2010-11-22
> **mc4man said:**
> Several ways - don't have any .jar's on hand to test

Globally for all users
Open the .desktop for java and edit the Exec= to remove the cautious launcher from lauch command

```
gksudo gedit /usr/share/applications/openjdk-6-java.desktop
```
change the line
Exec=cautious-launcher %f /usr/lib/jvm/java-6-openjdk/bin/java -jar
to
Exec=/usr/lib/jvm/java-6-openjdk/bin/java -jar

You could do the above but just with a local version of the .desktop, seen in screen as OpenJDK Java Free 6 Runtime, only available to you (basically the same as the custom command

thank you it works for Openjdk Java 
but what about sun Java 6 runtime as sun java works faster here

---

