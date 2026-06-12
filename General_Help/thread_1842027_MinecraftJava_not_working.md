---
title: "Minecraft/Java not working"
date: 2011-09-10
forum: General Help
---

### Post by DaimyoKirby on 2011-09-10
I'm running Ubuntu 11.04.

I tried to open Minecraft, and it seems to log in ok, and download (most of) the packages ok, but then it goes to the purple error screen and displays this error:
> 

      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 9/10/11 2:41 PM

Minecraft: Minecraft Beta 1.7.3
OS: Linux (i386) version 2.6.38-11-generic
Java: 1.6.0_22, Sun Microsystems Inc.
VM: OpenJDK Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:294)
	at net.minecraft.client.Minecraft.run(SourceFile:716)
	at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT 1e817ac6 ----------



Anyone know what's going wrong?

---

### Post by Zephemeros on 2011-09-12
It appears you are not running the latest version of Java. Try updating your Java version.

run the following in the terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

and that should update you to the latest version.

---

### Post by DaimyoKirby on 2011-09-18
Just remembered to follow up:

I did that, and that may have helped, but it appears the (main) problem was that minecraft.net was having trouble keeping up with the amount of people using/downloading from the site.

Thanks!

---

