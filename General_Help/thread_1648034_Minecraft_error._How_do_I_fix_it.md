---
title: "Minecraft error. How do I fix it?"
date: 2010-12-18
forum: General Help
---

### Post by enbokavmig on 2010-12-18
I can't play Minecraft (Alpha) on my computer with Ubuntu 10.10 (32-bit desktop edition). How do I fix it? I've sent an email to [email]support@mojang.com[/email] but they haven't replied. Thanks in advance. :D

--- BEGIN ERROR REPORT a1dce528 --------
Generated 2010-12-18 13:39

Minecraft: Minecraft Alpha v1.2.6
OS: Linux (i386) version 2.6.35-23-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:197)
    at net.minecraft.client.Minecraft.run(SourceFile:559)
    at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT 8253e4d1 ----------

---

### Post by DarkAmbient on 2010-12-18
read somewhere that sun java is needed to play Minecraft. (Instead of openJDK)

Info on how to install it easy, iI think it works in 10.10 aswell. [http://help.ubuntu.com/community/Java](http://help.ubuntu.com/community/Java)

You probably need to remove OpenJDK and IcedTea to prevent conflicts though.

But then again, I'm not 100% sure thats the problem... maybe someone else got a better solution.




EDIT: found a easier way to install Sun Java in Ubuntu10.10. 

(I guess it would be the best to uninstall OpenJDK & IcedTea first, you can do it in the Software Center)

Then, enable the Canonical-Partners repositories in the Software Center (its under edit->repositories).

after that, in terminal, enter:

```
sudo apt-get update && sudo apt-get install sun-java6-jre sun-java6-plugin
```

Then allow your Minecraft.jar to be executable by rightclick and click properties. Then find the option for that under the third/middle tab. (Sorry I dont know what its named in english, got swedish Ubuntu)

Then choose to open it with 'Sun Java 6 Runtime'.

---

