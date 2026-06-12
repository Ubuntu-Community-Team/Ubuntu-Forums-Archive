---
title: "Minecraft.jar not running"
date: 2011-01-24
forum: General Help
---

### Post by Markn951 on 2011-01-24
Hi guys,

So basically, I'm trying to run minecraft.jar. The download page states that the .jar is executable, but when I try to run it it's as if it was a tarball rather than an executable file. I don't want to extract anything, I want to run it. I tried the instructions on the website: ```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
``` but that didn't work, and I got this error:

> Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: net.minecraft.LauncherFrame.  Program will exit.

I also tried just ```
java minecraft.jar
``` and I get an error very similar to the one above. I'm not really sure what's wrong. I am in the directory that the .jar file is located, before you ask.

Thanks.

---

### Post by TeoBigusGeekus on 2011-01-24
Try
```
java -jar minecraft.jar
```

---

### Post by Markn951 on 2011-01-24
> **TeoBigusGeekus said:**
> Try
```
java -jar minecraft.jar
```

Many thanks, sir!

---

### Post by MACRULESANDISWAYBETTER on 2011-02-09
Im having the same problem, but java -jar minecraft.jar didnt work for me

---

### Post by FB91 on 2011-11-23
> **MACRULESANDISWAYBETTER said:**
> Im having the same problem, but java -jar minecraft.jar didnt work for me

(it's case sensitive)

---

### Post by TomAnkcorn on 2011-11-23
Right click on the jar. Then go into properties and select mark as executable. Then while also in properties go to the open with section and make the java runtime default.

---

### Post by oldtimer7777 on 2011-11-23
This fixed it for me:

[https://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](https://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)

---

