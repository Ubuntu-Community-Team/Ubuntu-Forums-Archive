---
title: "Minecraft Error, Help me!!"
date: 2011-07-28
forum: General Help
---

### Post by tnq67985 on 2011-07-28
Let me start off that I'm a beginner to Ubuntu, just not sure if I should put this in absolute beginner chat or General Help, Decided on General Help, Move me if I was wrong.


Anyways I have been trying for several days since getting Ubuntu 11.04 (I wouldn't be having problems but since my Windows 7 Ultimate crashed and wouldn't start up, Have to use Ubuntu until we can afford to get it again) So, I have finally gathered enough posts together to actually start the application in general, but after I start it, It updates (Downloads) and then a black screen for a few seconds, then I get an error. The error is as stated below.


Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 7/28/11 12:34 PM

Minecraft: Minecraft Beta 1.7.3
OS: Linux (amd64) version 2.6.38-10-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:294)
	at net.minecraft.client.Minecraft.run(SourceFile:716)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 93cca9ff ----------





I'm not sure what it means so help me if you can, I have learned enough from browsing other forums and topics that I should state my graphics card info and stuff, so I will:


I have an nVidia GeForce GTX 260M 1GB graphics card, 
My processor is Intel Core 2 Duo

Tell me if you need more, and how to get it, As I said I am VERY new to Ubuntu so I only know some very basic commands for the terminal.

Thanks in advance!!

---

### Post by Theredbaron1834 on 2011-07-29
Do you have java installed? If so, what one? Is it open java, or sun java? Cause I couldn't get Minecraft to work with open java, I think you have to use sun java. Search jre in synaptic, and see if you have sun or open. If you have open, uninstall it. It may be open source, but it isn't a perfect copy of sun's, so not all things work on it.

---

