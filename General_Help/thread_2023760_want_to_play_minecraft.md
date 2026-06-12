---
title: "want to play minecraft"
date: 2012-07-12
forum: General Help
---

### Post by Costa123 on 2012-07-12
I recently go a new laptop the u410 and installed ubuntu 12.04
I then installed openjdk java and tried to play minecraft after the login I got this error message


   Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.




--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 12/07/12 9:32 PM

Minecraft: Minecraft 1.2.5
OS: Linux (amd64) version 3.2.0-26-generic
Java: 1.6.0_24, Sun Microsystems Inc.
VM: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:236)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT 9a4afc5 ----------

when i looked it up people were saying to upgrade the videocard but my laptop is new

---

### Post by holycow131415 on 2012-07-12
Download: [http://www.lwjgl.org/download.php](http://www.lwjgl.org/download.php)

The latest as of this post is 2.8.4.

Extract the files anywhere.

Go into .minecraft folder

Overwrite the Mojang files in .minecraft/bin with those in  lwjgl-2.8.4/jar and .minecraft/bin/natives with lwjgl-2.8.4/native/linux.

---

### Post by Hydera5 on 2012-07-12
And if that doesn't work. You can try to run the .exe in wine. :wink:

---

### Post by Costa123 on 2012-07-13
i cant find mojang files in .minecraft/bin
thanks in advance:confused:

---

### Post by holycow131415 on 2012-07-13
Go to View > Show hidden files.

folders with a period in front of them are hidden. .minecraft is in your home directory.

---

### Post by Costa123 on 2012-07-14
thanks ill try that

---

