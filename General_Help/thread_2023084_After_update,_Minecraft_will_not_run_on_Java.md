---
title: "After update, Minecraft will not run on Java"
date: 2012-07-12
forum: General Help
---

### Post by Becarem on 2012-07-12
My copy of Minecraft was working perfectly, last night...until I  absentmindedly updated my Ubuntu 11.10.  Now, all I get after login is this:

      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 7/11/12 10:22 PM

Minecraft: Minecraft 1.2.5
OS: Linux (i386) version 3.0.0-22-generic-pae
Java: 1.6.0_23, Sun Microsystems Inc.
VM: OpenJDK Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: X Error - disp: 0x8c0f120 serial: 36 error:  BadRequest (invalid request code or no such operation) request_code: 157  minor_code: 14
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(L  inuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultP  eerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(Linux  DisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(Linux  Display.java:684)
    at org.lwjgl.opengl.Display.create(Display.java:854)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:236)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT 9c35562d ----------

I know for a fact that it was working on my 11.10 Ubuntu, through  OpenJDK Java 6 Runtime, as of last night.  Now I cannot even play single  player mode.  Since looking up error code 157, I believe it has something to do with an update involving Java.  Can anyone please help direct me to the solution?

---

### Post by Becarem on 2012-07-12
Update:

Essentially, I am having trouble getting both Java and Adobe Flash to work. I have a list of the recent updated files from last night available, but I have no way of sifting them for exactly which one is the cause of my video troubles.  What would do you suggest? Is there a way I can run a diagnostic to troubleshoot this?

Oneiric Ocelot 11.10
ATI Mobility Radeon HD 4250

Thank you!

---

### Post by Becarem on 2012-07-12
Updated my fglrx driver, that fixed my issue. Thank you!

---

