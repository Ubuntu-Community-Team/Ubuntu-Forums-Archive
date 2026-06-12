---
title: "Minecraft Help?"
date: 2012-09-28
forum: General Help
---

### Post by PizzaLover101 on 2012-09-28
Dunno if anyone can help me, but all I get is crashing.
Running Ubuntu 12.04
I tried reinstalling java 7 runtime and deleting the .minecraft folder, but still get the following message:

"

      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem; Failed to start game
This error has been saved to /home/jon/.minecraft/crash-reports/crash-2012-09-28_16.15.34-client.txt for your convenience. Please include a copy of this file if you report this crash to anyone.



--- BEGIN ERROR REPORT 77c330ed --------
Generated 28/09/12 4:15 PM

- Minecraft Version: 1.3.2
- Operating System: Linux (amd64) version 3.2.0-32-generic
- Java Version: 1.6.0_24, Sun Microsystems Inc.
- Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
- Memory: 30272432 bytes (28 MB) / 58720256 bytes (56 MB) up to 643170304 bytes (613 MB)
- JVM Flags: 0 total; 
- LWJGL: 2.4.2
- OpenGL: ~ERROR~ NullPointerException: null
- Is Modded: Probably not
- Type: Client
- Texture Pack: ~ERROR~ NullPointerException: null
- Profiler Position: N/A (disabled)[failed to get system properties (java.lang.NullPointerException)]


org.lwjgl.LWJGLException: X Error - disp: 0x7fc7182f2a80 serial: 31 error: BadRequest (invalid request code or no such operation) request_code: 153 minor_code: 14
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:233)
	at net.minecraft.client.Minecraft.run(SourceFile:516)
	at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT fb833224 ----------
"

"---- Minecraft Crash Report ----
// Sorry :(

Time: 28/09/12 4:15 PM
Description: Failed to start game

org.lwjgl.LWJGLException: X Error - disp: 0x7fc7182f2a80 serial: 31 error: BadRequest (invalid request code or no such operation) request_code: 153 minor_code: 14
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:233)
	at net.minecraft.client.Minecraft.run(SourceFile:516)
	at java.lang.Thread.run(Thread.java:679)

Relevant Details:
- Minecraft Version: 1.3.2
- Operating System: Linux (amd64) version 3.2.0-32-generic
- Java Version: 1.6.0_24, Sun Microsystems Inc.
- Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
- Memory: 30272432 bytes (28 MB) / 58720256 bytes (56 MB) up to 643170304 bytes (613 MB)
- JVM Flags: 0 total; 
- LWJGL: 2.4.2
- OpenGL: ~ERROR~ NullPointerException: null
- Is Modded: Probably not
- Type: Client
- Texture Pack: ~ERROR~ NullPointerException: null
- Profiler Position: N/A (disabled)"

---

