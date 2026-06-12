---
title: "Minecraft fail, help?"
date: 2012-01-16
forum: General Help
---

### Post by Nuncia on 2012-01-16
Ive been trying to get Minecraft to work on 11.10, ive installed java and wine and tried a bunch of things.... this is the error code i keep getting for the game, which happens right after i log in, before the usual Mojang screen;

```
[B]Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to support@mojang.com.
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 16/01/12 11:10 PM

Minecraft: Minecraft 1.1
OS: Linux (i386) version 3.0.0-14-generic
Java: 1.6.0_23, Sun Microsystems Inc.
VM: OpenJDK Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
OpenGL: Mesa DRI Intel(R) 845G x86/MMX/SSE2 version 1.3 Mesa 7.11, Tungsten Graphics, Inc

java.lang.RuntimeException: org.lwjgl.LWJGLException: X Error - disp: 0x9781370 serial: 91 error: BadDrawable (invalid Pixmap or Window parameter) request_code: 136 minor_code: 8
    at org.lwjgl.opengl.Display.update(Display.java:677)
    at org.lwjgl.opengl.Display.update(Display.java:657)
    at org.lwjgl.opengl.Display.initContext(Display.java:910)
    at org.lwjgl.opengl.Display.create(Display.java:861)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at net.minecraft.client.Minecraft.a(SourceFile:198)
    at net.minecraft.client.Minecraft.run(SourceFile:648)
    at java.lang.Thread.run(Thread.java:679)
Caused by: org.lwjgl.LWJGLException: X Error - disp: 0x9781370 serial: 91 error: BadDrawable (invalid Pixmap or Window parameter) request_code: 136 minor_code: 8
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxContextImplementation.nSwapBuffers(Native Method)
    at org.lwjgl.opengl.LinuxContextImplementation.swapBuffers(LinuxContextImplementation.java:75)
    at org.lwjgl.opengl.Context.swapBuffers(Context.java:163)
    at org.lwjgl.opengl.Display.swapBuffers(Display.java:646)
    at org.lwjgl.opengl.Display.update(Display.java:675)
    ... 7 more
--- END ERROR REPORT 447cafb7 ----------
[/B]
```Can anyone please tell me whats going wrong with this, what i can do to fix it with detailed instructions, or at least point me in the right direction??

---

