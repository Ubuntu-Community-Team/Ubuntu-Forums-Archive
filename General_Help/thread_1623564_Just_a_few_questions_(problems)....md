---
title: "Just a few questions (problems)..."
date: 2010-11-16
forum: General Help
---

### Post by Googie2149 on 2010-11-16
1. When I try to install WINE from the Ubuntu Software Center, I get this message (copied as best I could):
```
Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
V Details
ttf-symbol-replacement wine wine1.2 winetricks wisotool

```How can I fix this?

2. In an earlier version (9.10, I think), Ubuntu would tell me that there were proprietary drivers available for my graphics card. When I had it, I was able to use desktop effects. With 10.10, it no longer asks me if I want the drivers. Is this because the driver hasn't been updated for this release?

3. I have trouble running Java applets and applications. When I try to run any applets in Firefox, all I get is either a black or white screen. When I try to run an application (specifically, Minecraft), I get this error:
```


      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to support@mojang.com.
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 11/16/10 3:56 AM

Minecraft: Minecraft Alpha v1.2.2
OS: Linux (i386) version 2.6.35-22-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:201)
    at net.minecraft.client.Minecraft.run(SourceFile:563)
    at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT af62d1c6 ----------



```I'm thinking that I need to install the official JVM (not OpenJDK) to get it to work, I just don't know how in Ubuntu.

4. I have performance issues with games, websites, flash, and videos. It might just be my computer being old, though.

---

### Post by cinohpa on 2010-11-16
1. Have you tried enabling additional repositories? Maybe universe and/or multiverse are needed? Not really sure which you need as I don't use wine but it sounds like that sort of problem. 

Look here for this: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

2. How old is your graphics card? Maybe it isn't supported anymore. Is it ati/nvidia? The open drivers for ati have gotten a lot better. Did you try explicitly looking for drivers under system > administration > hardware drivers? 

3. I too have encountered bugs with openjdk. I figured out how to install the sun jvm by googling around for it. There is plenty of info about that elsewhere.

4. If your machine was working fine before you upgraded (I am guessing you recently upgraded ubuntu) then it is probably more of a driver/java issue. All of the problems you are mentioning here (games, websites, flash, videos) are things affected by the things you were asking about previously. Try fixing those first and then try to give more detail on what specifically isn't behaving.

---

### Post by Googie2149 on 2010-11-17
1. I have tried that, same error.

2. It would make sense that it is no longer supported as it is very old. It's a nvidia geforce mx 4000 (or something like that). I have tried going to the hardware drivers. It's an empty list. I'm going to see if the one on the nvidia website works.

3. I got the sun jvm, but I get the same error. I'm going to try running a few different applications, though.

4. I sorta upgraded. I had used ubuntu in the past, but I was trying different linux distributions so I had just migrated from fedora to this. I never used flash very much in any of the other linux distributions, but I did use it in windows. I could run all those things decently well (flash is worse than I would like, though).

---

