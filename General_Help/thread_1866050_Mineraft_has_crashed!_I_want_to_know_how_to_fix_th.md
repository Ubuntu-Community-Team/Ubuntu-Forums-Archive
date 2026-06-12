---
title: "Mineraft has crashed! I want to know how to fix this"
date: 2011-10-20
forum: General Help
---

### Post by ViiWee on 2011-10-20
Well I just got linux ubunu and i followed another helper on ubunu and so theen i started minecraft and logged in and then it said 
Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 10/20/11 5:21 PM

Minecraft: Minecraft Beta 1.8.1
OS: Linux (amd64) version 2.6.35-30-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:233)
    at net.minecraft.client.Minecraft.run(SourceFile:629)
    at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT dc634fde ----------


So if someone could help i would reatly appreciate it im 11 and looooooooooovvvvvvvvvvvve technology.......................also aht are beans and if they are like a ranking system and i can help give them ill give them you tthe person who helped me.:D

---

### Post by Snowboi on 2011-10-20
> **ViiWee said:**
> Well I just got linux ubunu and i followed another helper on ubunu and so theen i started minecraft and logged in and then it said 
Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 10/20/11 5:21 PM

Minecraft: Minecraft Beta 1.8.1
OS: Linux (amd64) version 2.6.35-30-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:233)
    at net.minecraft.client.Minecraft.run(SourceFile:629)
    at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT dc634fde ----------


So if someone could help i would reatly appreciate it im 11 and looooooooooovvvvvvvvvvvve technology.......................also aht are beans and if they are like a ranking system and i can help give them ill give them you tthe person who helped me.:D

this isn't the minecraft forums lol
but i personally play minecraft and i guess i can help you :D

First thing you can do is

backup your minecraft.jar

go into your home folder
hit ctrl + h at the same time
find .minecraft

(IF you installed any mods)
then go into bin
and save minecraft.jar somewhere else safe (not in .minecraft)
(only save your minecraft.jar if you installed any mods or anything)

(IF you wanna save your worlds)
stay in your .minecraft then go into saves
save those in a safe place (not in .minecraft)

now delete .minecraft and click the launcher again (the file you downloaded should be minecraft.jar) double click it and log in.
it should work now

be sure to put your saves and bin files back afterwards

---

